# AI Song Agent — 다운로드

주제 한 줄로 **가사 · 번역 · SUNO Style 프롬프트**를 만들고, 오디오를 붙여 **가사 싱크 뮤직비디오**까지 뽑는 데스크톱 앱입니다.

> 이 저장소는 **설치 파일 배포 전용**입니다. 소스 코드는 [ChanGeunPark/AISongAgent](https://github.com/ChanGeunPark/AISongAgent)에 있습니다.

---

## 1단계 — 앱 다운로드

### 👉 [**최신 버전 받으러 가기**](https://github.com/ChanGeunPark/AISongAgent-dist/releases/latest)

릴리스 페이지 아래쪽 **Assets**에서 내 기기에 맞는 파일을 받으세요.

| 내 기기 | 받을 파일 | 설치 방법 |
|---|---|---|
| **맥** (M1 이후, Apple Silicon) | `AI.Song.Agent_<버전>_aarch64.dmg` | 더블클릭 → `AI Song Agent`를 `Applications` 폴더로 드래그 |
| **Windows** (64bit) | `AI.Song.Agent_<버전>_x64_en-US.msi` | 더블클릭 → 안내대로 설치 (권장) |
| **Windows** (64bit) | `AI.Song.Agent_<버전>_x64-setup.exe` | msi가 막히는 환경에서 대신 사용 |

**지원 대상**

- **맥**: Apple Silicon(M1 이후)만 지원합니다. 왼쪽 위  → "이 Mac에 관하여" → **칩**에 "Apple M..."이 보이면 실행됩니다. Intel 맥용 빌드는 제공하지 않습니다.
- **Windows**: 64비트(x64)만 지원합니다.
- 영상 내보내기에 쓰는 **ffmpeg는 앱 안에 들어 있습니다.** 따로 설치할 필요 없습니다.

이전 버전이 필요하면 [전체 릴리스 목록](https://github.com/ChanGeunPark/AISongAgent-dist/releases)에서 받으세요.

---

## 2단계 — AI CLI 설치 (`claude` 또는 `codex` 중 **하나**)

이 앱에는 **API 키를 넣는 칸이 없습니다.** 대신 내 컴퓨터에 깔린 `claude` 또는 `codex` 명령을 직접 실행해서 가사를 만듭니다.
그래서 **둘 중 하나는 반드시 설치·로그인**되어 있어야 합니다. (둘 다 깔면 앱에서 골라 쓸 수 있습니다.)

### 방법 A — Claude CLI (권장)

**macOS**

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

**Windows (PowerShell)**

```powershell
irm https://claude.ai/install.ps1 | iex
```

설치가 끝나면 터미널(Windows는 PowerShell)에서 `claude`를 **한 번 실행**해 로그인합니다 — Claude 계정 또는 Anthropic API 키.

확인:

```bash
claude --version
```

### 방법 B — Codex CLI

```bash
npm install -g @openai/codex     # Node가 있을 때
brew install codex               # macOS, Node 없이
```

로그인 (둘 중 하나):

```bash
codex login                      # ChatGPT Plus/Pro/Team 계정
export OPENAI_API_KEY=sk-...     # 또는 API 키
```

확인:

```bash
codex --version
```

> 앱이 CLI를 찾는 위치: PATH 전체, `~/.local/bin`, `~/.cargo/bin`, npm 전역 폴더, macOS의 `/Applications/Codex.app`.
> 위 방법대로 설치하면 자동으로 잡힙니다.

---

## 3단계 — 실행

- **macOS**: Spotlight(`Cmd + Space`)에서 "AI Song" 검색 후 실행
- **Windows**: 시작 메뉴에서 "AI Song Agent" 실행

앱 우측 상단 **CLI 셀렉터**에서 설치한 CLI(`claude` / `codex`)를 고르면 준비 끝입니다.
설치되지 않은 CLI는 회색 + 빨간 점으로 표시되어 선택할 수 없습니다.

---

## (선택) 4단계 — SUNO 연동 크롬 확장

앱에서 만든 **제목·가사·스타일을 suno.com 만들기 화면에 버튼 한 번으로** 채워 넣고,
완성된 곡의 **가사 타이밍을 앱으로 가져오는** 크롬 확장입니다.
**설치하지 않아도 앱은 정상 동작합니다** — 복사·붙여넣기가 번거로울 때만 쓰세요.

1. [릴리스 페이지](https://github.com/ChanGeunPark/AISongAgent-dist/releases/latest)의 Assets에서
   **`AI.Song.Agent.Extension_*.zip`** 을 받아 압축을 풉니다.
2. 크롬 주소창에 `chrome://extensions` 입력 → 우상단 **개발자 모드**를 켭니다.
3. 좌상단 **압축해제된 확장 프로그램을 로드합니다** → 방금 압축을 푼 폴더를 선택합니다.

설치 후 SUNO 만들기 화면 우하단에 **♪ 앱 가사 채우기** 버튼이 생깁니다.
앱 결과 화면의 **[SUNO로 보내기 ↗]** 를 누르면 열려 있는 SUNO 탭에 자동으로 채워집니다.

> 크롬을 켤 때마다 "개발자 모드 확장 프로그램을 사용 중지하시겠습니까?" 배너가 뜹니다.
> **사용 중지를 누르지 말고 X로 닫으면** 그대로 쓸 수 있습니다. (웹스토어 등록을 준비 중이며, 등록되면 이 배너가 사라집니다.)

---

## ⚠️ 처음 한 번은 OS 경고가 뜹니다

배포용 코드 서명을 하지 않은 앱이라, **최초 1회**만 OS가 실행을 막습니다. 한 번 넘겨주면 이후로는 그냥 열립니다.

### macOS

`AI Song Agent.app`을 **우클릭 → 열기 → "그래도 열기"**.

그래도 "손상되었습니다 / 개발자를 확인할 수 없습니다"라며 안 열리면 터미널에서:

```bash
xattr -d com.apple.quarantine "/Applications/AI Song Agent.app"
```

실행 후 다시 열면 됩니다.

### Windows

"Windows에서 PC를 보호했습니다" 창이 뜨면 **추가 정보 → 실행**을 누릅니다.

---

## 이 앱으로 할 수 있는 것

**작사**

- 언어 선택: **한국어 / 영어(PopSong) / 일본어(J-Pop)**
  영어·일본어는 한국어로 먼저 작사한 뒤 자연스럽게 2차 번역합니다.
- 결과 카드: **제목 / 한국어 가사 / 번역 가사 / Style 프롬프트** — 카드마다 복사 버튼
- 가사는 SUNO 섹션 태그(`[Verse 1]`, `[Chorus]` …)를 포함해 그대로 붙여넣을 수 있습니다.
- 수정 지시를 넣어 다시 생성할 수 있고, 버전 기록이 남습니다.

**라이브러리**

- 생성한 곡은 자동으로 로컬에 저장됩니다(저장 버튼 없음). 제목·주제·가사 통합 검색 지원.
- 곡에 오디오 파일을 첨부할 수 있습니다.

**뮤직비디오**

- 오디오를 들으며 탭으로 **가사 싱크**를 찍고, 자막을 얹은 영상으로 내보냅니다.
- 배경 이미지·영상, 텍스트 효과, 스티커, 타임라인 편집 지원. 내보내기는 내장 ffmpeg가 처리합니다.

**커스터마이즈**

- 설정창에서 4개 시스템 프롬프트(한국어 작사 / 영어 번역 / 일본어 번역 / Style 생성)를 직접 편집할 수 있습니다.
- 자주 쓰는 Style 프롬프트를 **북마크**로 저장해 두고 곡마다 골라 쓸 수 있습니다.

---

## 안 될 때

| 증상 | 해결 |
|---|---|
| 앱에서 "선택한 CLI가 PATH에 없습니다" | 터미널에서 `claude --version`(또는 `codex --version`)이 되는지 먼저 확인하세요. 잘 되면 **앱을 완전히 종료했다 다시 실행**합니다. 방금 CLI를 설치했다면 터미널과 앱을 모두 새로 열어야 합니다. |
| macOS에서 앱이 "손상됨"이라며 안 열림 | 위의 `xattr -d com.apple.quarantine ...` 명령을 실행하세요. |
| 생성 중 인증 / 로그인 에러 | 터미널에서 `claude`(또는 `codex login`)를 한 번 실행해 로그인 상태를 확인하세요. |
| 맥에서 dmg가 안 열림 | Intel 맥은 지원하지 않습니다. Apple Silicon(M1 이후)인지 확인하세요. |
| 생성이 30초~2분씩 걸림 | 정상입니다. CLI가 모델 응답을 기다리는 시간입니다. |
| 확장이 "앱에 연결하지 못했어요" | 앱이 켜져 있어야 합니다. 앱을 실행한 뒤 SUNO 페이지를 새로고침하세요. |
| 확장을 깔았는데 SUNO에 버튼이 안 보임 | `chrome://extensions`에서 확장이 **사용 설정** 상태인지 확인하고, SUNO 페이지를 새로고침하세요. |

---

## 데이터는 어디에 저장되나요

곡·설정·북마크·영상 프로젝트는 모두 **내 컴퓨터에만** 저장됩니다. 별도 서버로 전송하지 않습니다.

| OS | 위치 |
|---|---|
| macOS | `~/Library/Application Support/com.parkchangeun.aisongagent/` |
| Windows | `%APPDATA%\com.parkchangeun.aisongagent\` |

곡은 JSON 파일 하나씩이라, 이 폴더를 Dropbox·iCloud Drive로 연결해 두면 백업·기기 간 동기화도 됩니다.

---

## 문의 · 버그 신고

- 사용 중 문제나 제안: [AISongAgent 저장소 이슈](https://github.com/ChanGeunPark/AISongAgent/issues)
- 개발 문서 / 소스에서 직접 빌드: [AISongAgent](https://github.com/ChanGeunPark/AISongAgent) 저장소의 `docs/SETUP.md`
