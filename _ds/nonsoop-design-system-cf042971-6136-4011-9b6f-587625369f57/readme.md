# 논숲 (Nonsoop) Design System

AI 채점 기반 대학 입시 논술 학습 플랫폼의 디자인 시스템. 학생이 논술 문제를 응시하고 AI 피드백으로 성장하는 B2C 웹 서비스를 위한 토큰·컴포넌트·UI 킷 모음입니다.

> **Brand keywords:** Trust (신뢰) · Growth (성장) · Approachable (친근)
> "논숲은 수많은 논술 콘텐츠가 모인 학습의 숲입니다. 하나의 문제는 하나의 나무가 되고, 학생은 그 나무들을 하나씩 가꾸며 자신만의 숲을 만들어 갑니다."

## Source

- **Figma:** `[Design] 논숲 (복사).fig` — 사용자가 첨부한 파일(가상 파일시스템으로 마운트). 페이지: `00_Branding`, `02_Foundation`, `03_Components`, `04_Page`, `page`, `page2`. 이 시스템은 이 파일에서 직접 추출·머티리얼라이즈되었습니다. (읽기 접근이 없는 독자를 위해 출처만 기록합니다.)
- 토큰(296 Figma Variables · 7 컬렉션 · 다중 모드)과 컴포넌트(약 95개 패밀리)는 모두 이 파일이 정답(source of truth)입니다.

## Index / Manifest

- `styles.css` — 글로벌 CSS 진입점. 소비 프로젝트는 이 파일 하나만 링크합니다. (`@import` 목록만 포함)
- `tokens/` — `fonts.css`(웹폰트), `fig-tokens.css`(Figma 변수 296개, 색/스페이싱/반경/투명도/아이콘 + dark·test-ios·brand 모드), `typography.css`(타입 스케일 + `.type-*` 유틸리티), `brand.css`(브랜드 그린 앵커 + 링크 색).
- `components/` — 재사용 UI 프리미티브 (React `.jsx` + `.d.ts` + `@dsCard` HTML). `Mascot/`은 하위 폴더.
- `guidelines/` — Colors·Type·Spacing·Brand 파운데이션 스펙 카드.
- `ui_kits/nonsoop-web/` — 실제 제품 화면 재현 (클릭 가능한 프로토타입).
- `assets/` — 마스코트 렌더 등 브랜드 비트맵.
- `SKILL.md` — Claude Code / Agent Skills 호환 진입점.

## Components

Icons (Lucide 기반, currentColor): `IconActionFunnel`, `IconActionX`, `IconActionX2`, `IconCustomAI2`, `IconCustomClock`, `IconCustomHeart`, `IconCustomSmile`, `IconGeneralBookOpen`, `IconGeneralBookmark`, `IconGeneralEllipsis`, `IconGeneralFolderOpen`, `IconGeneralMapPin`, `IconGeneralMessageSquareMore`, `IconGeneralMessageSquareMore2`, `IconGeneralUser`, `IconNavigationArrowRight`, `IconNavigationChevronLeft`, `IconNavigationChevronRight`, `IconNavigationExpandDown`, `IconNavigationExpandDown2`, `IconNavigationExpandUp`, `IconNavigationExpandUp2`, `IconNavigationLogOut`, `IconNavigationSearch`, `IconStatusCheck`, `IconStatusCheck2`, `IconStatusCheckRing`, `IconStatusCheckRing2`, `IconStatusCircleX`, `IconStatusInfo`, `IconStatusInfo2`, `IconStatusTriangleAlert`, `IconStatusTriangleAlert2`, `IconButton`.

Actions: `Button`, `Button2`, `Button3`, `ButtonFilter`.

Forms & selection: `Input`, `DropdownField`, `Dropdown`, `DropdownMenu`, `DropdownOption`, `Checkbox`, `RadioButton`, `Switch`, `Chip`, `Badge`, `ExamTypeBadge`, `FilterOptionBox`, `Filter`.

Feedback & overlay: `Toast`, `InlineAlert`, `Notice`, `Dialog`, `Tooltip`, `Tooltip2`, `Spinner`, `ProgressBar`, `Indicator`.

Navigation & structure: `Tab`, `Accordion`, `PaginationNumber`, `PaginationArrow`, `BannerPagination`, `PageCount`, `Carousel`, `CarouselNumber`, `Floating`, `FloatingMenu`, `FloatingTopButton`, `GNB`, `GNBText`, `GNBProfile`, `GNBProfileName`, `GNBDropdownItem`, `LNBText`, `ProfileDropdown`, `ProfileItem`, `Footer`, `Container`.

Data & domain: `Card`, `CardModal`, `CardFavorite`, `CardUniBadge`, `ExamCard`, `EmptyState`, `MetaRow`, `TopRanking`, `RakingRow`, `RakingNumber`, `BodyCell`, `HeaderCell`, `Text`, `RedDescription`, `Vector15`, `Frame427319733`, `Component4`.

Brand: `Logo` ('N' 모티브 로고마크 + 논숲 워드마크), `Mascot` (완두콩이).

### Intentional additions
- **`Mascot`** — 완두콩이 마스코트를 브랜드 렌더 PNG로 감싼 래퍼 컴포넌트. Figma는 이 캐릭터를 벡터/이미지로 정의하지만 코드용 단일 진입점이 없어, Empty State·온보딩에서 재사용하도록 추가했습니다.
- 깨진 벡터로 추출된 일부 Lucide 아이콘(chevron·info·check·alert)은 동일한 Lucide 패스로 정리했습니다 (ICONOGRAPHY 참고).

---

## CONTENT FUNDAMENTALS

논숲의 카피는 **한국어 존댓말(-요/-습니다체)** 기반의 학습 서비스 톤입니다.

- **인칭:** 서비스가 사용자에게 말하는 2인칭 안내체. "입력하세요", "확인해주세요", "제출해주세요". 사용자를 '학생'으로 지칭하되 화면에서는 직접 호칭을 거의 쓰지 않음.
- **어조:** 신뢰감 있고 담백함. 과장·감탄사·이모지 없음. 위험 행동(제출)은 단정하게 경고: "답안 제출 후에는 수정이 불가합니다. 신중하게 제출해주세요."
- **격식:** 액션 라벨은 짧은 동사구 ("응시하기", "답안 제출", "채점 결과 보기"). 짧을수록 좋음.
- **긍정 피드백:** 성장 서사와 연결 ("꾸준한 연습이 성장을 만듭니다", "저장되었습니다."). 마스코트 완두콩이가 Empty State에서 친근함을 더함.
- **숫자·메타:** 대학명·연도·문제 수 등 사실 정보 위주 ("고려대학교 · 2025 · 3문제"). 불필요한 통계·과시성 수치 지양.
- **이모지:** 사용하지 않음. 상태 표현은 아이콘 + 색으로 처리.
- **혼용:** 서비스 명사/기능명은 한국어, 브랜드 키워드(Trust/Growth/Approachable)와 'AI'는 영문 그대로.

## VISUAL FOUNDATIONS

**색 (Color)**
- **Primary #008B48 (신뢰 그린)** — 핵심 CTA·브랜드·포커스. 9단계 스케일(`--primary-100…900`). hover는 한 단계 진하게(#007A3F), pressed는 더 진하게(#006535).
- **Accent #B5E82A (성장 라임)** — 포인트/강조/마스코트. 넓은 면적보다 포인트로 사용.
- **Neutral Gray** — 텍스트/보더/서피스 (`--gray-100…900`, #F9FAFB → #111827). 본문 #111827, 보조 #4B5563, 3차 #6B7280.
- **Semantic** — Success #0AAD5E, Error #FF4747, Warning #EFAC03, Info #0847A6. 각 100(배경)/500(강조) 쌍.
- **University badge** — 대학 논술 카드용 4색: Green #006B3D, Blue #009BCB, Navy #004E96, Red #AC0027. Secondary 퍼플 #795ED6.
- 이미지: 마스코트는 라임그린 톤의 밝고 따뜻한 3D 렌더. 사진 이미지는 거의 쓰지 않음.

**타입 (Type)**
- **Pretendard** = UI/본문 전면. Medium(500) 기본, SemiBold(600) 제목/강조, Bold(700) 큰 제목, Regular(400) 보조.
- **SUIT** = 로고·대형 디스플레이 전용 (40/50/60px, Bold).
- 스케일: 12·14·16·17·18·20·22·24·26·30 / 40·50·60. 자간 -0.3~-0.4px(한글 최적화), 행간 본문 1.5·제목 1.4·브랜드 스토리 1.7.

**스페이싱 & 반경**
- 4px 베이스 그리드: 4·6·8·12·16·20·24·32·40·48·56·64·80.
- 반경: 4·8·12·20·24, 그리고 999(full/pill). 버튼 8·12, 카드 12~16, 칩/스위치 999.

**표면·그림자·보더**
- 카드는 흰 배경 + 얇은 보더(`--border-default` #E5E7EB) 또는 옅은 그림자(`rgba(17,24,39,0.12)` 계열). 강한 그림자 지양.
- 포커스: 2px inset 링(`--border-focus` = 브랜드 그린). 오류: `--border-error`.
- 인풋/드롭다운: 1px 보더, 포커스 시 브랜드 그린 보더.

**모션·상태**
- 트랜지션은 짧고 담백(색/투명도 위주). 과한 바운스·회전 없음.
- Hover: 배경 한 단계 진하게 또는 서피스 톤 변화. Pressed: 더 진한 톤(스케일 shrink는 쓰지 않음). Disabled: 회색 배경 + 회색 텍스트.
- **Toast:** 하단 중앙 오버레이, 기본 3초 / Close·Action 있으면 5초.
- **Dialog:** 가로형 기본, 왼쪽 보조 액션 / 오른쪽 주요 액션.
- **Alert:** 자동으로 사라지지 않으며 액션 최대 1개.
- 핵심 CTA(응시하기, 답안 제출)는 항상 Primary 버튼.

**레이아웃**
- GNB(상단 글로벌 내비) + 콘텐츠 컨테이너 중심의 웹 레이아웃. Floating(우하단 상단이동/메뉴) 보조.

## ICONOGRAPHY

- **아이콘 시스템 = Lucide** (stroke 2, 24×24, round cap/join). Figma 파일의 아이콘 세트(약 1,790 글리프)는 Lucide 세트 전체입니다.
- 이 프로젝트는 실제 제품에서 쓰이는 브랜드·UI 아이콘만 컴포넌트로 재현했습니다(`Icon*` 컴포넌트, `currentColor`로 채색 — `style={{ color: '…' }}`). 넓은 범용 세트가 필요하면 **Lucide를 CDN(`lucide.dev`)에서 동일 stroke로 로드**하세요. 이는 대체가 아니라 원본 세트와 동일합니다.
- 추출 과정에서 지오메트리가 유실된 chevron·info·check·triangle-alert 아이콘은 표준 Lucide 패스로 다시 그렸습니다.
- 커스텀 글리프: `IconCustomAI2`(AI 채점), `IconCustomClock`, `IconCustomHeart`, `IconCustomSmile`. 대학 로고 등 3rd-party 마크는 포함하지 않았습니다.
- 이모지/유니코드 아이콘은 사용하지 않습니다.

## Logo & Brand assets

- **Logo** — 'N' 모티브. 라임그린+그린 두 개의 둥근 기둥이 겹쳐 성장/반복 모듈을 상징. 워드마크는 SUIT. 나무를 직접 그리지 않고 "성장이 쌓여 숲을 이루는 과정"을 단순 형태로 표현. (`components/Logo.jsx`)
- **완두콩이 Mascot** — 라임그린 완두콩 캐릭터. 포인트 시스템 마스코트, Empty State·온보딩에 사용. 실제 브랜드 렌더는 `assets/mascot-wandukong-3d.png`, `assets/mascot-wandukong-wave.png`.

## Usage

소비 프로젝트에서 `styles.css` 한 파일을 링크하고, 컴파일된 `_ds_bundle.js`를 로드한 뒤 `window.DesignSystem_cf0429`에서 컴포넌트를 읽어 사용합니다.

```html
<link rel="stylesheet" href="styles.css">
<script src="_ds_bundle.js"></script>
<script type="text/babel">
  const { Button, ExamCard, Toast } = window.DesignSystem_cf0429;
</script>
```
