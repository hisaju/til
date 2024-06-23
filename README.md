```mermaid
erDiagram
    USER {
        int id
        string name
        string email
        string password_hash
        string role
        datetime created_at
        datetime updated_at
    }
    
    STUDY_SESSION {
        int id
        string title
        string description
        datetime start_time
        datetime end_time
        int organizer_id
        string location
        datetime created_at
        datetime updated_at
    }
    
    STUDY_SESSION_PARTICIPANTS {
        int id
        int user_id
        int study_session_id
        datetime created_at
        datetime updated_at
    }
    
    ONLINE_LINK {
        int id
        int study_session_id
        string platform
        string link
        datetime created_at
        datetime updated_at
    }
    
    STUDY_PROGRESS {
        int id
        int user_id
        string current_study
        string goals
        string challenges
        datetime created_at
        datetime updated_at
    }
    
    DISCUSSION {
        int id
        int user_id
        string topic
        string content
        datetime created_at
        datetime updated_at
    }
    
    COMMENT {
        int id
        int discussion_id
        int user_id
        string content
        datetime created_at
        datetime updated_at
    }
    
    USER ||--o{ STUDY_SESSION_PARTICIPANTS : participates
    USER ||--o{ STUDY_PROGRESS : logs
    USER ||--o{ DISCUSSION : initiates
    USER ||--o{ COMMENT : writes
    STUDY_SESSION ||--o{ STUDY_SESSION_PARTICIPANTS : includes
    STUDY_SESSION ||--o{ ONLINE_LINK : has
    DISCUSSION ||--o{ COMMENT : receives
    STUDY_SESSION ||--|{ USER : organized_by
