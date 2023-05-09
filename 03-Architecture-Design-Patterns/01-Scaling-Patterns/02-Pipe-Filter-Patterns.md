# Pipes and Filters Patterns

Pipes and Filters Pattern은 데이터 처리를 여러 단계로 나누고, 각 단계를 처리하는 필터를 구성하여 데이터를 처리하는 패턴입니다. 데이터는 각 필터를 통과하며 필터에서는 입력 데이터를 가공하고 출력 데이터를 다음 필터에 전달합니다.

대표적인 예시로는 Unix 운영체제에서 사용되는 파이프라인 기능이 있습니다. 예를 들어, cat 명령어로 파일의 내용을 출력하고, 이를 grep 명령어로 필터링하고, 다시 sort 명령어로 정렬하여 출력하는 과정에서 파이프라인이 사용됩니다.

Pipes and Filters Pattern에서의 베스트 프랙티스는 다음과 같습니다.

모듈성: 각 필터는 입력 데이터와 출력 데이터를 정의하여 독립적으로 작동하므로, 모듈성이 높아져서 유지 보수 및 확장성이 용이해집니다.

재사용성: 필터는 단일 책임을 가지므로, 재사용이 가능하고, 각 필터의 조합으로 새로운 데이터 처리 기능을 만들 수 있습니다.

유연성: 필터는 각 단계마다 데이터를 가공하여 출력하므로, 각 단계의 구현 방식을 자유롭게 선택할 수 있습니다.

성능: Pipes and Filters Pattern은 다수의 작은 단위의 필터를 통해 데이터를 처리하기 때문에, 대용량 데이터 처리에도 높은 성능을 보장합니다.

테스트 용이성: 각 단계의 입력과 출력이 정의되어 있으므로, 단위 테스트를 쉽게 구성할 수 있습니다.


---------------------------------------

Pipes and Filters Pattern은 데이터를 처리하는 시스템에서 데이터 처리과정을 여러 단계로 나누어 필터 단위로 데이터를 처리하고, 이를 연결하여 데이터 처리를 완성하는 패턴입니다.

예를 들어, 데이터 추출, 전처리, 분석, 저장 등의 과정으로 이루어진 데이터 처리 시스템에서, 이를 Pipes and Filters Pattern으로 구현하면, 데이터 추출 필터, 전처리 필터, 분석 필터, 저장 필터로 나누어 각 단계를 처리하고, 필요한 경우 필터를 추가, 제거, 변경하여 데이터 처리 시스템을 유연하게 변경할 수 있습니다.

대표적인 예시로는 Unix 명령어에서 사용되는 Pipe 기능이 있습니다. 이는 여러 명령어를 파이프(|)로 연결하여 결과값을 전달하는 것입니다. 또한, AWS의 데이터 파이프라인과 같이 여러 단계로 이루어진 데이터 처리 작업에서도 Pipes and Filters Pattern이 적용됩니다.

Pipes and Filters Pattern에서의 베스트 프랙티스는 다음과 같습니다.

단일 책임 원칙: 필터는 입력 데이터에 대해서만 작업을 수행해야하며, 다른 필터의 역할까지 겹쳐서는 안 됩니다.

재사용성: 필터는 독립적인 단위로 작업을 수행하므로, 다른 프로젝트나 다른 데이터 처리 작업에서도 재사용이 가능합니다.

확장성: 필터를 추가하거나, 필터 내부 로직을 변경하여 작업을 변경할 수 있으므로, 시스템의 확장성을 향상시킬 수 있습니다.

유연성: 필터의 순서, 개수, 역할 등을 변경하여 데이터 처리 작업을 유연하게 변경할 수 있습니다.

테스트 용이성: 각 필터는 독립적인 단위로 작업을 수행하므로, 필터 단위의 테스트를 수행하여 전체 시스템의 품질을 개선할 수 있습니다.

