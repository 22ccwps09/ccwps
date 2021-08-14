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
- dark mode design 레이아웃을 적용해서 진행

## item-single.html
- 첨부된 youtube 링크와 시간 타임을 맞출 수 있는지 


# CCWPS도 고객과 화면을 확정한다. #40

## 추가자료
- [ ] 각 폴더를 대표하는 사진 2장씩 (한국전쟁 - 서비스를 하지 않더라도)
- [ ] 100개 아이템의 유투브 경로
- [ ] 엑셀 taxonomy write 형식


## 작업관련
- [x] 다크모드 디자인 관련 적용 완료. 
- [x] 유투브 시작시간 실행 방법 관련된 링크 확인
- [ ] 아이템 영상 아래쪽에 shotlist 삽입하는 방식(텍스트 슬라이드 )
- [ ] 장소 화면에 별도 UI 구성해 보기 https://leafletjs.com/examples/quick-start/
- [ ] 포스트 카테고리
- [ ] 포스트 카테고리에 tag를 써서 관련된 화면과 콘텐츠를 묶는 방식
- [ ] 편집가능한 tag 활용한 이벤트 컬렉션
- [ ] 엑셀 & 마크다운 동기화 관련 방식 (생성 스크립트라도 / 원본- 엑셀 / 수정본 - markdown file)
- [ ] 타입센스 검색엔진 테섭 / 검색엔진 react app 생성


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
- kctu로 연결 완료
- 80포트로 jydh 와 같이 2개 띄워 놓기
- 검색엔진 연결 (검색엔진쪽)