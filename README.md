# Tmux Configuration

이 문서는 개인화된 tmux 설정에 대한 설명입니다.

## 주요 기능

### 기본 설정
- **접두사 키(Prefix Key : PK) 변경**: 기본 `Ctrl+b`에서 `Ctrl+a`로 변경
- **설정 파일 다시 로드**: `PK + r`로 설정 파일 즉시 적용
- **마우스 지원**: 마우스로 패널 선택 및 크기 조정 가능
- **히스토리 버퍼**: 10,000줄까지 히스토리 저장
- **상태바 위치**: 화면 상단에 배치

### 키 바인딩
- `PK + h`: 왼쪽 패널로 이동
- `PK + j`: 아래쪽 패널로 이동
- `PK + k`: 위쪽 패널로 이동
- `PK + l`: 오른쪽 패널로 이동
- `PK + r`: 설정 파일 다시 로드

### 플러그인

#### 필수 플러그인
- **TPM** (Tmux Plugin Manager): 플러그인 관리자
- **tmux-sensible**: 합리적인 기본 설정 제공

#### 테마 및 UI
- **catppuccin/tmux**: Catppuccin Mocha 테마 적용
  - 둥근 모서리 윈도우 스타일
  - 세션명을 왼쪽 상태바에 표시

#### 시스템 모니터링
- **tmux-cpu**: CPU 사용률 표시
- **tmux-battery**: 배터리 상태 표시

#### 현재 tmux 환경(세션, 창, 팬, 레이아웃 등)을 저장하고 복원
- **tmux-resurrect**: 현재 tmux 환경(세션, 창, 팬, 레이아웃 등)을 저장하고 복원하는 핵심 기능을 제공
- **tmux-continuum**: tmux-resurrect의 확장 플러그인으로, 주기적으로 tmux 환경을 자동 저장하고, tmux 시작 시 자동으로 복원

### 상태바 구성

#### 왼쪽 상태바
- 세션 이름 표시

#### 오른쪽 상태바
- 애플리케이션 정보
- CPU 사용률
- 시스템 업타임
- 배터리 상태

## 설치 및 설정

### 1. TPM 설치
```bash
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
```

### 2. 설정 파일 적용
```bash
# tmux.conf를 홈 디렉토리에 복사
rm -f ~/.tmux.conf && curl -O https://raw.githubusercontent.com/Steve-Jeong/tmux/main/tmux.conf
mv tmux.conf ~/.tmux.conf

# tmux 재시작 또는 설정 다시 로드
tmux source-file ~/.tmux.conf
```

### 3. 플러그인 설치
tmux 세션 내에서:
1. `PK + I` (대문자 I)를 눌러 플러그인 설치
2. 설치 완료 후 tmux 재시작

## 터미널 요구사항
- 256색 지원 터미널 권장
- `tmux-256color` 터미널 타입 사용

## 사용법
1. tmux 시작: `tmux`
2. 새 세션 생성: `tmux new -s session_name`
3. 세션 연결: `tmux attach -t session_name`
4. 설정 다시 로드: `PK + r`

## 커스터마이징
- 접두사 키 변경: `set -g prefix` 값 수정
- 테마 변경: `@catppuccin_flavor` 값 변경 (mocha, latte, frappe, macchiato)
- 추가 플러그인: `set -g @plugin` 라인 추가 후 `PK + I`로 설치

## 문제 해결
- 플러그인이 로드되지 않는 경우: TPM이 올바르게 설치되었는지 확인
- 색상이 제대로 표시되지 않는 경우: 터미널의 256색 지원 확인
- 키 바인딩이 작동하지 않는 경우: 설정 파일 다시 로드 (`PK + r`)

