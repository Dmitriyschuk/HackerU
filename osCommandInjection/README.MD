# OS Command injection
## Sample code Java

><p>Process process = Runtime.getRuntime().exec(osCommand + data)
><br> process.waitFor();</p>

Необходимо избегать вызова оболочки команд ОС через функцию Runtime.exec. <br>
Для запуска команд использовать ProcessBuilder:<br>

><p>ProcessBuilder processBuilder = new ProcessBuilder();<br>
>Process p = processBuilder.command("osCommand", "data").start();</p>


## Sample code PHP

![image](https://user-images.githubusercontent.com/61540481/194315960-dc5af6cb-1041-4969-8193-d74ff152412a.png)
</p>
<p>В данном примере используется не безопасный пользовательский ввод.

Переменная $rootTestCmd собирается из нескольких источников:<br> 
фиксированных строк "sudo -S -u"  и "chmod 0755 /home 2>&1"<br>
параметра URL ($_GET['rootUname'])<br>

Команда exec выполняет внешнюю программу. Фактически команда которая должна быть выполнена зависит от пользовательского ввода. При этом никакой санитизации входных данных нет. Необходимо экранировать любые символы которые могут быть использованы для обмана шелл-команд.<br>
Исправление:<br>
Санитизируем переменную $rootUname.<br>
Для этого создаем новую переменную $sanitizeRootUname = escapeshellarg($rootUname)<br>
Передаем эту переменную в &rootTestCmd2 и далее в команду exec.</p>




