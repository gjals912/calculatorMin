# calculatorMin
calculator
fun main() {
        var calculatorMin =

        // 입력값 받기
        println("연산 할 첫번째 값을 입력")
        val num1: Int = Integer.parseInt(readLine())
        println("연산 할 두번째 값을 입력")
        val num2: Int = Integer.parseInt(readLine())

        var num3 = 0

        println("연산자를 입력해주세요 +,-,/,*")
        var calculationOption = readLine()!!.toInt()

        val calc = Calculation(num1, num2, calculationOption)

        // 첫 연산 시 서브 클래스별 연산 결과
        var additionResult = AddOperation(num1, num2).calculate()
        var subtractionResult = SubtractOperation(num1, num2).calculate()
        var multiplicationResult = MultiplyOperation(num1, num2).calculate()
        var divisionResult = DivideOperation(num1, num2).calculate()
        var calculationResult = 0
        var moreCalculationOption: Int = 0

        if (calculationOption == 1) {
            calculationResult = additionResult
            num3 = 0
        } else if (calculationOption == 2) {
            calculationResult = subtractionResult
            num3 = 0
        } else if (calculationOption == 3) {
            calculationResult = multiplicationResult
            num3 = 1
        } else if (calculationOption == 4) {
            calculationResult = divisionResult
            num3 = 1
        }

    val op: String? = readLine()
    val result =
        when (op){
            "+" -> num1 + num2
            "-" -> num1 - num2
            "*" -> num1 * num2
            "/" -> num1 / num2
            else -> throw Exception("op is wrong")
        }
            }

    open class Calculation(var num1: Int, var num2: Int, var operationOption: Int) {
        open fun calculate(): Int {
            println("연산중...")
            return 0
        }
    }

    class AddOperation(num1: Int, num2: Int) : Calculation(num1, num2, 1) {
        override fun calculate(): Int = num1 + num2
    }

    class SubtractOperation(num1: Int, num2: Int) : Calculation(num1, num2, 2) {
        override fun calculate(): Int = num1 - num2
    }

    class MultiplyOperation(num1: Int, num2: Int) : Calculation(num1, num2, 3) {
        override fun calculate(): Int = num1 * num2
    }

    class DivideOperation(num1: Int, num2: Int) : Calculation(num1, num2, 4) {
        override fun calculate(): Int = num1 / num2
    }
