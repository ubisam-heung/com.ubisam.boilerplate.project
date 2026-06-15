# com.ubisam.boilerplate.project

Boilerplate Project 생성 및 AI Agent 연동 가이드입니다.

---

## 1. 리포지토리 생성

GitHub에서 각자 프로젝트별 (현재 예시는 `com.ubisam.boilerplate.project` 입니다) 리포지토리를 생성합니다.

---

## 2. Branch Protection Ruleset 설정

생성한 프로젝트의 `main` 브랜치에 Ruleset을 추가합니다.

**Settings → Rules → Rulesets → New branch ruleset**

### 기본 설정

| 항목 | 값 |
|---|---|
| Ruleset Name | `main` |
| Enforcement status | **Active** ⚠️ (기본값 Disabled → 반드시 변경) |

### Target branches

**Add target → Default branch** 를 선택합니다.

### Branch rules 체크 항목

| 항목 | 설정 |
|---|---|
| Restrict deletions | ✅ |
| Require a pull request before merging | ✅ |
| Block force pushes | ✅ |

> **Require a pull request before merging** 선택 시 하위 옵션이 펼쳐집니다.  
> Required approvals는 `0`으로 두면 승인 없이 본인이 직접 merge 가능합니다.

설정 후 **Create** 버튼을 클릭합니다.

---

## 3. AI Agent 설치 및 Clone

AI Agent가 설치된 디렉토리의 `workspace` 안에 해당 리포지토리를 클론합니다.

```bash
cd <ai-agent>/workspace
git clone https://github.com/ubisam/com.ubisam.boilerplate.project
cd com.ubisam.boilerplate.project
```

---

## 4. 작업 브랜치 생성 및 Push

사용할 AI 도구에 따라 브랜치를 생성하고 원격에 등록합니다.

**Claude 사용 시**
```bash
git checkout -b claude
git push origin claude
```

**Codex 사용 시**
```bash
git checkout -b codex
git push origin codex
```

---

## 5. 작업 및 Pull Request

각 브랜치에서 AI Agent로 작업을 진행한 후 GitHub에서 Pull Request를 생성하여 `main`으로 merge 합니다.

> Branch Protection Rule에 의해 직접 push는 불가하며, PR을 통해서만 merge할 수 있습니다.

---

## 6. Merge 후 브랜치 동기화

PR merge 완료 후 작업 브랜치를 최신 `main` 상태로 동기화합니다.

**Claude 브랜치**
```bash
git checkout claude
git pull origin main
```

**Codex 브랜치**
```bash
git checkout codex
git pull origin main
```

---

## 작업 흐름 요약

```
main (보호됨)
 ├─ claude ──[작업]──▶ Pull Request ──▶ merge ──▶ git pull origin main
 └─ codex  ──[작업]──▶ Pull Request ──▶ merge ──▶ git pull origin main
```
