# 냉전평화연구센터 디지털아카이브

## 배포환경

- master -> netlify | ccwps.org
- develop -> cloudflare pages | ccwps.durumi.io
- develop -> ubuntu | ccwps.ap.ngrok.io


# Site-building

## tailwind-aa-theme

- 탐색
- 검색(hugo-search-fuse-js-aa) / 기본 검색을 붙인다. (100개 영상)

## taxonomy
- tag는 최상위에서 이벤트로 묶어야 할 때 사용.(subject와 중복)
- tag 화면을 다이나믹하게 보여줄 수 있는 방법 / 생각보다 태그 단어가 처음 생성되면


## Site-Building

- 소개 페이지 / 전체적인 자료와 리서치가이드를 작성하는 공간으로 변경
- 공지사항이 필요하다고 했던 점
- 로고 변경
- dark mode design 레이아웃을 적용해서 진행
 
## 추가자료
- [ ] 각 폴더를 대표하는 사진 2장씩 (한국전쟁 - 서비스를 하지 않더라도)
- [ ] 100개 아이템의 유투브 경로
- [ ] 100개 아이템의 물리적 파일을 다운로드 서비스 할 생각이 있는지 ? / 요청하는 방식으로 

## item-single.html
- 첨부된 youtube 링크와 시간 타임을 맞출 수 있는지 

# data

## s3 Rclone sync(with component url)
```
$ rclone sync --progress aa-data:ccwps /home/ubuntu/ccwps/content/items
$ rclone sync --progress /home/ubuntu/ccwps/content/items aa-data:ccwps
```
## 메타데이터
- 영상외에 비주얼 구성을 위한 사진
- 메타형식을 확정하기 위한 pdf 문서 (4-5개만 더 지정하면 좋겠다.)

## markedown_handler
- https://github.com/team-durumi/hugo_markdown_handler
```
ruby markdown_generator.rb -d '/home/ubuntu/ccwps/content/items' -r 'https://ccwps.s3.ap-northeast-2.amazonaws.com'
```

# develop

## Multipass

https://ubuntu.com/blog/using-cloud-init-with-multipass
```
multipass launch -n hugo --cloud-init hugo-typesense.yml --mem 4G --disk 10G
ngrok http --region=ap --hostname=ccwps.ap.ngrok.io 1313
```

# Production

```
hugo --gc --minify -d public;
```
- 아파치로 연결하는 것은 실패