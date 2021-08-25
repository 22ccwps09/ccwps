# 냉전평화연구센터 디지털아카이브

## 배포환경

- master -> netlify | ccwps.org
- prodcution | typesense -> aa-jydh | search.ccwps.org (타입센스 검색엔진)
- develop -> netlify | ccwps.durumi.io (배포 속도가 너무 느려서)
- develop | typesense -> aa-jydh | ts-ccwps.durumi.io (타입센스 검색엔진)


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

## 엑셀형식

- 전달해 주셨던 파일에 빨간색 탭이 추가된 열입니다.관리하시는 목록에 그대로 쓰시라고, 통합셀에 그대로 수정했습니다.(오픈된 것만 구분하지 않았음.)

- (생성형태-수집/기증/소장)대부분 수집으로 복붙해주시면 됩니다. (내부 관리 문서에도 넣으시는걸 추천)

- (공개여부-TRUE/FALSE)주황색으로 표시해주셨던 항목이 TRUE로 적혀있으면 됩니다. 

- (생산일-1952-00-00)날짜형식을 하나로 맞춰주세요. 1952-00-00 형태로 부탁드립니다. (언제부터 언제까지인 날짜 형식이 포함되어 있는 케이스가 있는데 조사된 정보는 메타에 추가로 옮겨주시고, 시작날짜를 지정해 주세요.)

- (생산장소, 생산기관, 촬영자, 주제)는 모두 태그형식으로 사용됩니다. 다수의 단어를 넣을 수 있습니다. 주실 때 ,(콤마)로 표시해서 전달해주시면 저희가 일괄 |(구분자)로 변경해서 사용하겠습니다. 내부 규칙을 |(구분자)로 잡아주시면 좋습니다. (형식 :  파주 선유리 유엔군임시사령부, 판문점 -> 파주 선유리 유엔군임시사령부|판문점 )

- F 기준에 "주제, 태그"는 포함되어 있지 않은데 추가되어 있습니다. 현재의 시리즈 구분이 주제로 되어 있으니, 추가가 없으시다면 시리즈에 적힌 값을 그대로 주제에 사용합니다. 태그는 말씀드렸던데로 "오픈이벤트, 심포지움컬렉션" 처럼 자연적으로 발생하는 이벤트 혹은 태그 컬렉션을 표현하는데 사용하고자 합니다. (추후 작성도 괜찮음. )

- 미디어 형식이 추가되었습니다. 

- 유투브 : https://www.youtube.com/embed/MXPOgefJSqE 

- 원본파일 주소 : 사진 아이템 10개 정도를 오픈하면 해당 사진은 다운로드 링크가 생기게 되는데, 말씀드렸던 클라우드(S3)의 다운로드 경로가 됩니다. 이번에는 무시하셔도 됩니다.

## 추가자료
- [x] 각 폴더를 대표하는 사진 2장씩 (한국전쟁 - 서비스를 하지 않더라도)
- [x] 100개 아이템의 유투브 경로
- [x] 엑셀 taxonomy write 형식


## 작업관련
- [x] 다크모드 디자인 관련 적용 완료. 
- [x] 유투브 시작시간 실행 방법 관련된 링크 확인
- [x] 장소 화면에 별도 UI 구성해 보기 https://leafletjs.com/examples/quick-start/
- [x] 타입센스 검색엔진 테섭 / 검색엔진 react app 생성
- [x] 편집가능한 tag 활용한 이벤트 메뉴로 활용
- [x] 엑셀 & 마크다운 동기화 관련 방식 (생성 스크립트라도 / 원본- 엑셀 / 수정본 - markdown file)
- [ ] 쌍 따옴표 처리 

# data

## s3 Rclone sync(with component url)
```
$ rclone sync --progress aa-data:ccwps /home/ubuntu/ccwps/content/items
$ rclone sync --progress /home/ubuntu/ccwps/content/items aa-data:ccwps
```
## 메타데이터
- 영상외에 비주얼 구성을 위한 사진
- 메타형식을 확정하기 위한 pdf 문서 (4-5개만 더 지정하면 좋겠다.)

## Markdown Generator using comma separated values.
```
$ cd path/to/this/repo
$ ruby csv_converter.rb -f '/Users/woonjjang/hugo/ccwps/static/ccwps-items-210825.csv' -d '/Users/woonjjang/hugo/ccwps/content/items' -t 'venues sources creators'
```

# develop

## Multipass

https://ubuntu.com/blog/using-cloud-init-with-multipass
```
multipass launch -n hugo --cloud-init hugo-typesense.yml --mem 4G --disk 10G
ngrok http --region=ap --hostname=ccwps.ap.ngrok.io 1313
```

## typesense-search
- multipass 환경에서 접근
```
$ sudo systemctl status typesense-server.serv 

``
# Production

```
hugo --gc --minify -d public;
```
- kctu로 연결 완료
- 80포트로 jydh 와 같이 2개 띄워 놓기
- 검색엔진 연결 (검색엔진쪽)