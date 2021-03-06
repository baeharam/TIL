깃을 다루다 보면 다양한 커맨드를 사용하거나 과거의 기록을 사용할 때 HEAD를 사용하는 경우가 빈번하다. 특히나 캐럿(^)이나 틸드(~)까지 붙어서 나오게 되면 뭐가 뭔지 상당히 헷갈리기 때문에 정리해두는 것이 좋다.

## HEAD

가장 최신의 커밋을 가리킨다. `git reset` 과 같이 쓸 때 상당히 헷갈렸는데, `git reset 커밋` 의 뜻이 해당 커밋으로 리셋시킨다는 의미이니 여기선 최신 커밋을 가리키는 HEAD를 사용하면 안된다. 어쨌든 가장 최신의 커밋을 가리키는 것이며 HEAD가 바뀐 히스토리를 보려면 `git reflog` 를 사용하면 된다.

<br>

## HEAD^ vs HEAD~

캐럿(^)과 틸드(~) 모두 부모를 가리킨다는 점에서 그 의미는 동일하지만 1개만 쓸 경우와 2개 이상 쓸 경우가 다르다. 1개만 쓸 경우엔 모두 바로 위 부모 커밋을 가리킨다는 점에서 같다. 하지만 2개 이상부터는 캐럿의 경우 n번째 부모를 뜻하지만 틸드의 경우 n번째 상위 부모를 뜻한다. Stackoverflow의 [답변](https://stackoverflow.com/a/43046393/11789111) 을 보면, 그 차이를 확실히 알 수 있다. Merge를 하면서 부모 커밋이 여러개 생길 수 있는 경우가 있기 때문에 이 차이를 확실히 알아둬야 유용히 사용할 수 있다.