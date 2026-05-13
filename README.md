# Cursor Skill Framework

Bộ rules + docs để AI làm việc hiệu quả, đúng mục đích từ prompt đầu tiên.

---

## Cách setup

### 1. Copy vào project mới
```
project-root/
├── CLAUDE.md                   ← Điền thông tin project vào đây
├── .cursor/
│   └── rules/
│       ├── 00-core.mdc         ← Luôn active, hành xử cơ bản
│       ├── 01-feature.mdc      ← Skill thêm feature
│       ├── 02-bug.mdc          ← Skill fix bug
│       ├── 03-init.mdc         ← Skill init project mới
│       └── 04-review.mdc       ← Skill review code
└── vibe/
    ├── SPEC.md                 ← Toàn bộ scope project
    ├── TASKS.md                ← Task tracker
    └── ARCHITECTURE.md         ← Quyết định kỹ thuật
```

### 2. Điền CLAUDE.md trước
Điền đầy đủ: tên project, tech stack, architecture, off-limits areas.
AI đọc file này đầu tiên trong mỗi session.

### 3. Điền SPEC.md
Liệt kê tất cả tính năng Phase 1, acceptance criteria, và out of scope.

---

## Trigger commands

```
init: [mô tả app]           → Khởi động project từ đầu
feature: [tên tính năng]    → Build feature mới
bug: [mô tả lỗi]            → Fix bug có quy trình
review: [phase/feature]     → Review code, phase gate
```

---

## Workflow chuẩn

```
Dự án mới:
  init: → (AI hỏi requirements) → (tạo docs) → confirm → setup

Mỗi tính năng:
  feature: → (AI show plan) → confirm → build → review:

Khi có bug:
  bug: → (AI investigate) → (show root cause) → confirm → fix
```

---

## Rules quan trọng

- AI **không được code** trước khi show plan và được confirm
- AI **chỉ sửa** files được liệt kê
- AI **không tự refactor** code ngoài scope
- **Có P0 bug** → blocked, không sang phase tiếp theo
