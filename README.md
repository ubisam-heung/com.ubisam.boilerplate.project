# com.ubisam.boilerplate.project

Boilerplate Project 생성 및 AI Agent 연동 가이드입니다.

---

## 1. 리포지토리 생성

GitHub에서 `com.ubisam.boilerplate.project` 리포지토리를 생성합니다.

---

## 2. Branch Protection Rule 설정

`main` 브랜치에 아래 규칙을 추가합니다.

**Settings → Branches → Add branch ruleset**

| 항목 | 설정 |
|---|---|
| Require a pull request before merging | ✅ |
| Require branches to be up to date before merging | ✅ |
| Require conversation resolution before merging | ✅ |
| Do not allow bypassing the above settings | ✅ |

설정 후 **Save** 합니다.

---

## 3. AI Agent 설치 및 Clone

AI Agent가 설치된 디렉토리의 `workspace` 안에 리포지토리를 클론합니다.

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
