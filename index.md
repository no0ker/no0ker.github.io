## Небольшие комментарии к заданию #3

Внимание! 
Это не готовый код - не нужно его копировать. А если и будете копировать, то обратите внимание, что некоторые куски кода здесь опущены, так что подумать все равно придется =)

### Шаг 1.
Само деление не представляет интереса. Интерес представляет только вывод результата. Приступаем соответственно к нему. Пишем код, который напрашивается сразу же.

```markdown
public class PrettyFormatter {
    public List<String> format(ResultDto resultDto) {
    }
}

class ResultDto {
}
```

### Шаг 2.
Добавляем вывод делимоого.
В дтошку добавляем поле.
```markdown
public class ResultDto {
    private long divident;
}
```
Добавляем вывод этого поля.
```markdown
public class PrettyFormatter {
    public List<String> format(ResultDto resultDto) {
        ...
        addDivident(result, resultDto);
        ...
        return result;
    }
    
    private void addDivident(List<String> result, ResultDto divident) {
        String row = result.get(0);
        String changedRow = insert(row, divident.getDivident(), 1);
        result.add(0, changedRow);
    }
    
    private String insert(String sourceString, Object value, int position) {
        ...
    }
}
```

### Шаг 3.
Оцениваем читабельность кода и смотрим результат.
Читабельные названия методов? Вроде, да
Читабельные методы? Ну, они короткие, вроде, понятные. Да.

### Шаг 4.
Добавялем к результату вывод делителя и частного.
```markdown
    public List<String> format(ResultDto resultDto) {
        ...
        addDivident(result, resultDto);
        addDivider(result, resultDto);
        addResult(result, resultDto);
        ...
    }
```
Соответственно и в ДТО нужно добавить некоторые поля..

### Шаг 5.
Оцениваем читабельность.
Понятно, что делает каждая строка? Ну, вроде да. Добавляем делимое, делитель и частное.


### Шаг 6.
Понятно, что в процессе вывода у нас есть "повторяющиеся блоки".
Значит, ДТО нужно поправить
```markdown
    public class ResultDto {
        private long divident;
        private long divider;
        private long result;
        private List<StepDto> steps;
}
```
и вывод тоже нужно подправить
```markdown
    public List<String> format(ResultDto resultDto) {
        addDivident(result, resultDto);
        addDivider(result, resultDto);
        addResult(result, resultDto);
        for (StepDto step : resultDto.getSteps()) {
            addStep(result, step);
        }
        return result;
    }
```

### Шаг 7.
Вспомнить про палочки и символы подчеркивания. 
