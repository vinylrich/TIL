# Golang에서 []byte

## golang에서 byte slice를 사용하는 함수가 많은 이유

Go언어의 string값은 불변하기 때문! 값을 변경 할 수 없고, 더 작게 만들거나, 크게 만들 수 없음

그렇기 때문에 []byte값으로 변경 후 값을 변경하고 []byte값에서 string값으로 다시 변경해서 사용하는 것!