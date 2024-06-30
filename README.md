# barbearia-interativa
// . A barbearia que faz interação entre indivíduos/clientes, através da troca de dados e/ou informações. Além de um espaço social que conectará instituições de acolhimento e profissionais que quiserem se voluntariar.
import java.util.Scanner

// Classe para representar um cliente
data class Cliente(val nome: String, val horario: String)

fun main() {
    val scanner = Scanner(System.`in`)
    val clientes = mutableListOf<Cliente>()

    println("Bem-vindo à Barbearia!")

    while (true) {
        println("\nO que você gostaria de fazer?")
        println("1. Agendar um horário")
        println("2. Ver horários agendados")
        println("3. Sair")

        when (scanner.nextInt()) {
            1 -> agendarHorario(clientes, scanner)
            2 -> mostrarHorarios(clientes)
            3 -> {
                println("Obrigado por visitar a Barbearia!")
                return
            }
            else -> println("Opção inválida, por favor, escolha novamente.")
        }
    }
}

// Função para agendar um horário
fun agendarHorario(clientes: MutableList<Cliente>, scanner: Scanner) {
    println("\nPor favor, digite seu nome:")
    val nome = scanner.next()

    println("Por favor, digite o horário desejado:")
    val horario = scanner.next()

    clientes.add(Cliente(nome, horario))
    println("Horário agendado com sucesso para $nome às $horario!")
}

// Função para mostrar os horários agendados
fun mostrarHorarios(clientes: List<Cliente>) {
    if (clientes.isEmpty()) {
        println("\nNão há horários agendados no momento.")
        return
    }

    println("\nHorários agendados:")
    clientes.forEachIndexed { index, cliente ->
        println("${index + 1}. ${cliente.nome} - ${cliente.horario}")
    }
}

