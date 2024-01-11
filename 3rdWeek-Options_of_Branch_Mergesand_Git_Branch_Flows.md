
# CodeitSprint_WeeklyPaper-3rd
About Option of Branch Merges and Git Flow Branch

## Option of Brnach Merges
Merge는 한 Branch와 다른 Branch를 병합할 때에 사용하는 명령어이다.

이때, Pull Request를 이용한 Merge는 단순 Merge를 포함하여 Commit History를 남기는 방식과 연관하여 세가지 방법이 있다.

### Merge
  - 제일 단순한 PR Merge 방식.
  - Fork되었던 버전의 Commit 변동 사항을 손을 대지 않고 그대로 유지하면서 본 작업물에 병합.
  - 모든 Commit과 Branch의 흔적이 남으므로 작업 흐름을 파악하기 좋지만, Commit History가 난잡해질 가능성이 높다. - 장점이 곧 단점이 될 수 있음.
  
### Squash and Merge
  - 분기되었던 Commit이나 Branch들을 모두 합쳐 하나의 Commit으로 병합.
  - 의미있는 Commit 하나만을 남겨 History가 과도하게 난잡해지는 현상을 방지.
  - History를 남기지 않고 한 Commit만을 남기므로, Commit의 상세 내용 검수에 과한 소비가 발생 가능.
   
### Rebase and Merge
  - 분기된 Branch의 Commit들을 초기 Branch의 최신 Commit을 Main으로 하여, 분기되었던 Commit을 차례로 Merge하는 것.
  - Merge Commit을 남길 필요가 없는 Merge에 사용하면 좋으며, Commit History가 깔끔해지면서도 각 Commit의 내용 확인이 용이.
  - Rebase를 통해 옮겨진 Commit들은 Hash 값이 변경되므로, 차후 Hash값을 통한 History 추적에 영향을 줄 수 있음.

## Git Branch Flows
Git Flow Branch는 Main Branch와 Development Branch를 유지하며, 용도에 따른 상세 Branch를 생성하는 방식이다.

대략적인 용도에 따라 다음과 같이 나뉜다.

> Main - 정식 배포중인 소스 코드
> 
> Develop - 개발중인 코드를 관리하는 Branch.
> 
> Feature - 개발 기능을 관리하는 Branch. 개발이 완료된 기능은 Develop로 Merge 된 후 제거됨.
> 
> Release - 배포를 준비하는 Branch. 차기 버전의 모든 기능 개발 완료시 Main 및 Develop 에 Merge전 마무리 작업 및 버그 수정을 실시함. 작업 완료할 경우 제거됨.
> 
> Hotfix - Main 소스 코드에서 발생한 긴급 버그 수정을 위한 Branch. 버그 해결 이후 Main과 Develop로 Merge됨. 빠른 버그 대응을 위한 Brnach.

이를 이용해 얻는 장점과 단점은 다음과 같다.

### 장점
- 안정적인 배포 구조가 갖춰짐.
- 긴 개발주기에 적합 / 복잡한 기능 개발과 버그 수정에 유용.

### 단점
 - 주요 Branch가 증가함에 따라 작업 관리의 효율 감소.
 - 소형 프로젝트에 부적합.
