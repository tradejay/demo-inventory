# Google Apps Script (GAS) Backend API

Google Sheets를 고가용성 DB로 활용하고, Google Drive를 스토리지로 연결하여 $0 서버리스 백엔드를 구현한 스크립트입니다.

## 주요 기능
- **RESTful API 액션 핸들러**: `doGet`, `doPost` 기반 CRUD 및 OAuth 2.0 JWT 교환
- **PDF/이미지 자동 생성**: 템플릿 스프레드시트 복제 -> 데이터 바인딩 -> Google Drive PDF/PNG 내보내기
- **동시성 및 락 제어**: `LockService`를 통한 시트 동시 쓰기 경합 방지
- **캐싱 및 웜업**: `CacheService`를 통한 메타데이터 및 권한(ACL) 캐싱

## 배포 및 환경설정 (Script Properties)
Google Apps Script 에디터의 **Project Settings > Script Properties**에 다음 키를 등록하세요:
- `DEFAULT_SHEET_ID`: 메인 장비 재고 및 대여 시트 ID
- `TEMPLATE_SPREADSHEET_ID`: 대여증 서식 시트 ID
- `TEMPLATE_SHEET_GID`: 대여증 탭 GID
- `PDF_FOLDER_ID`: 생성된 대여증 PDF가 저장될 Google Drive 폴더 ID
- `SHEET_FOLDER_ID`: 사본 시트가 저장될 Google Drive 폴더 ID
- `GOOGLE_CLIENT_ID`: Google OAuth Web Client ID
- `GOOGLE_CLIENT_SECRET`: Google OAuth Web Client Secret
