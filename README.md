# windows-test
<!DOCTYPE html>
<html lang="kk">
<head>
<meta charset="UTF-8">
<title>Windows орнату тесті</title>
<style>
body { font-family: Arial; background:#f4f4f4; padding:20px; }
.container { background:#fff; padding:20px; max-width:900px; margin:auto; border-radius:8px; }
.question { margin-bottom:15px; }
.correct { color:green; font-weight:bold; }
.wrong { color:red; font-weight:bold; }
#timer { font-size:20px; color:red; text-align:right; }
button { padding:10px 20px; font-size:16px; }
</style>
</head>
<body>

<div class="container">
<h2>Windows операциялық жүйесін орнату тесті</h2>

<div id="timer">15:00</div>

<p>
Аты-жөні: <input type="text" id="name"><br><br>
Тобы: <input type="text" id="group">
</p>

<form id="quiz">

<script>
const questions = [
["Windows операциялық жүйесін орнату үшін не қажет?", ["Антивирус","Драйвер пакеті","Орнату дискісі немесе флешка","Тек интернет"], 2],
["Компьютер Windows орнатуды бастау үшін қай режимде жүктелуі керек?", ["Sleep Mode","Boot Mode","Safe Mode","Hibernate"], 1],
["BIOS/UEFI баптауларында бірінші болып не таңдалады?", ["Қатты диск","Орнату тасымалдаушысы","Оперативті жад","Бейне карта"], 1],
["Windows орнату кезінде дискіні бөлу қай кезеңде жасалады?", ["Тіл таңдау","Қайта жүктеу","Дискіні таңдау","Лицензия келісімі"], 2],
["Windows орнату файлының кеңейтімі қандай?", [".zip",".exe",".iso",".rar"], 2],
["«Format» командасы не үшін қолданылады?", ["Дискіні тазалау","Файлдарды көшіру","Дискіні бөлу","Деректерді сақтау"], 0],
["Windows орнату уақыты орташа қанша уақыт алады?", ["1–5 минут","10–30 минут","2 сағат","1 сағат"], 1],
["Windows орнатылғаннан кейін ең алдымен не орнату керек?", ["Браузер","Ойындар","Драйверлер","Антивирус"], 2],
["NTFS деген не?", ["Бағдарлама","Вирус","Драйвер","Файлдық жүйе"], 3],
["Product Key не үшін қажет?", ["Жүйені баптау","Жүйені көшіру","Жүйені іске қосу","Жүйені өшіру"], 2],
["Windows орнату кезінде тіл параметрі қашан таңдалады?", ["Ортада","Орнату соңында","Қайта жүктегенде","Орнату басында"], 3],
["Орнату кезінде компьютер неше рет қайта жүктелуі мүмкін?", ["5 рет","Қайта жүктелмейді","1 рет","2–3 рет"], 3],
["Windows орнатуға арналған ресми құрал қалай аталады?", ["Task Manager","Media Creation Tool","Control Panel","Device Manager"], 1],
["«Custom» орнату нұсқасы нені білдіреді?", ["Жаңарту","Қалпына келтіру","Қолмен орнату","Автоматты орнату"], 2],
["Windows 10 орнатуға ең аз талап етілетін жад көлемі қандай?", ["512 МБ","1 ГБ","8 ГБ","2 ГБ"], 3],
["Орнату кезінде интернет не үшін қажет болуы мүмкін?", ["Міндетті","Экран үшін","Драйверлерді жүктеу үшін","Қайта жүктеу"], 2],
["Қазіргі Windows жүйесінің нұсқасы:", ["Windows XP","Windows 8","Windows 11","Windows 10"], 2],
["Қате дискіні таңдап орнатудың салдары қандай?", ["Интернет өшеді","Мәліметтер жоғалуы мүмкін","Жүйе тез жұмыс істейді","Өзгеріс жоқ"], 1],
["Windows орнату аяқталғанын не көрсетеді?", ["BIOS","Қара экран","Жұмыс үстелі","Қайта жүктеу"], 2],
["Windows жүйесін қайта орнату не үшін жасалады?", ["Монитор","Баяулату","Қателерді жою","Вирус көбейту"], 2]
];

questions.forEach((q,i)=>{
document.write(`<div class="question"><b>${i+1}. ${q[0]}</b><br>`);
q[1].forEach((a,j)=>{
document.write(`<label><input type="radio" name="q${i}" value="${j}"> ${a}</label><br>`);
});
document.write(`</div>`);
});
</script>

<button type="button" onclick="finish()">Тестті аяқтау</button>
</form>

<div id="result"></div>
</div>

<script>
let time = 900;
const timer = setInterval(()=>{
let m = Math.floor(time/60);
let s = time%60;
document.getElementById("timer").innerText = `${m}:${s<10?"0"+s:s}`;
time--;
if(time<0){ clearInterval(timer); finish(); }
},1000);

function finish(){
let correct=0, output="";
questions.forEach((q,i)=>{
let ans = document.querySelector(`input[name=q${i}]:checked`);
if(ans && parseInt(ans.value)===q[2]){
correct++;
output+=`<p class="correct">${i+1}. Дұрыс</p>`;
}else{
output+=`<p class="wrong">${i+1}. Қате (Дұрыс жауап: ${q[1][q[2]]})</p>`;
}
});
document.getElementById("result").innerHTML =
`<h3>Нәтиже</h3>
<p>Аты-жөні: ${name.value}</p>
<p>Тобы: ${group.value}</p>
<p><b>Дұрыс жауаптар: ${correct} / 20</b></p>` + output;
}
</script>

</body>
</html>
