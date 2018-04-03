---
layout: post
title: "[Git] .gitignore 수정 후 적용하기"
tags: [git]
---

`.gitignore`에 등록함으로써 특정 파일을 형상관리에서 제외할 수 있습니다. 
Local 개발환경에서만 필요한 파일(thumb.db 등)이 있을 경우 편리한 기능입니다.
그러나 `.gitignore`에 등록을 했는데 반영이 되지 않는 경우가 있어서 해결방법을 포스팅합니다.

## 원인
한 번 git에 업로드한 것을 `.gitignore`에 추가했을 경우 발생합니다. 
캐시에 해당 파일의 인덱스가 남아있기 때문에 추가된 `.gitignore`의 설정이 반영되지 않았던 것입니다.

## 해결책
`.gitignore`에 추가된 리스트를 반영 시키기 위해서는 쉘에서 다음과 명령어를 실행합니다.

```sh
git rm -r --cached .
git add .
git commit -m "your commit message”
```

이후 Push를 하면 Remote에도 적용이 됩니다. 

검색해 보면 금방 나오는 간단한 방법이지만 잊어버리지 않기 위해 정리해 보있습니다.