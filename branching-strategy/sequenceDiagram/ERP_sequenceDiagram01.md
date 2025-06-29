``` mermaid
 sequenceDiagram
    participant D as 開發人員
    participant F as feature/*
    participant Dev as develop
    participant RM as 發佈經理
    participant R as release/*
    participant M as main
    participant H as hotfix/*

    loop 功能開發
    D->>Dev: 從 develop 建立 feature 分支
    D->>F: 在 feature 分支上開發
    D->>Dev: 建立 Pull Request (PR)
    Note over Dev: 程式碼審核 (Code Review)
    Dev-->>F: 合併 PR 到 develop
    end

    loop 版本發佈
    RM->>Dev: 從 develop 建立 release 分支
    Note over R: QA 測試與 Bug 修復
    RM->>M: 合併 release 到 main
    RM->>M: 標記版本 (Tag)
    RM->>Dev: 合併 release 回 develop
    end

    loop 緊急修復
    D->>M: 從 main 建立 hotfix 分支
    D->>H: 在 hotfix 分支上修復
    D->>M: 合併 hotfix 到 main
    D->>M: 標記新版本 (Tag)
    D->>Dev: 合併 hotfix 回 develop
    end
```
