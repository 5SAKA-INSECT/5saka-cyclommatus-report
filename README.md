# 5saka Cyclommatus report — v3

## 지금 바로 미리보기 (갤럭시·PC)

`index.html` 한 개만 Chrome으로 엽니다. 오프라인 상태에서도 메뉴, 검색, 관리자 미리보기, 글 작성·수정·삭제, 사진·표 추가, 댓글 승인·삭제를 시험할 수 있습니다. 상단 **관리자**를 누르면 오프라인 체험용 관리자로 전환됩니다. 이 기능은 **실제 인증이 아니며** 로컬 브라우저에만 저장됩니다. Chrome 브라우저 데이터를 지우거나 기기를 바꾸면 시험 데이터가 사라질 수 있습니다. 작은 사진만 시험하세요.

## 실제 운영 준비

1. Supabase 새 프로젝트 생성 후 `schema.sql`을 SQL Editor에서 실행합니다.
2. Authentication → Users에서 본인 계정을 생성하고 ID(UUID)를 확인합니다.
3. SQL Editor에서 `insert into public.site_admins(user_id) values ('본인-UUID');` 실행합니다.
4. Project Settings → API에서 **Project URL**과 **anon/publishable key**만 복사합니다. `service_role` 또는 secret 키는 절대 복사하지 않습니다.
5. `index.html`의 `const CONFIG={supabaseUrl:'',supabaseAnonKey:''}` 두 문자열에 값을 넣습니다.
6. GitHub **공개** 저장소에 `index.html`을 올리고 Settings → Pages → Deploy from branch → main / root를 선택합니다. 공개할 때는 관리자 이메일·비밀번호를 소스에 넣지 않습니다.
7. 운영 화면 상단 '관리자'에서 이메일/비밀번호로 로그인합니다. 데이터베이스 RLS가 게시글 생성·수정·삭제, 댓글 승인·삭제, 이미지 업로드를 관리자만 허용합니다.

## 주의

- 방문자는 로그인 없이 댓글을 제출합니다. 공개는 관리자 승인을 거칩니다. 악성 댓글·스팸 방지를 위해 운영 전 Supabase 또는 Cloudflare 등의 CAPTCHA/속도제한 장치가 필요합니다. 현재 버전에는 CAPTCHA가 없습니다.
- 업로드 이미지는 공개 저장소에서 불러옵니다. 민감한 자료를 업로드하지 마세요.
- `index.html`을 직접 여는 오프라인 모드와 실제 배포 모드는 데이터가 연동되지 않습니다. 정식 사용 전에 온라인으로 직접 글 작성·수정·사진 업로드·댓글 접수·승인을 한 번씩 시험하세요.
- 전자게시판 운영과 개인정보 수집 관련 현지 법규를 확인하세요. 댓글 작성자에게 개인정보를 요구하지 않습니다.
- 기본 메뉴 학명은 사용자가 제공한 36개 항목을 사용하였고, 분류학적 유효성 검증을 뜻하지 않습니다.
