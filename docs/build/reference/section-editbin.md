---
title: /SECTION (EDITBIN)
ms.date: 11/04/2016
f1_keywords:
- /section
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
ms.openlocfilehash: 8bcc925b34118630c872a0147b93291626b7c19b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822434"
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)

```
/SECTION:name[=newname][,attributes][alignment]
```

## <a name="remarks"></a>Uwagi

Tej opcji zmienia atrybuty sekcji, zastępując atrybuty, które zostały ustawione po sekcji w pliku o obiekt został skompilowany lub połączone.

Po dwukropku ( **:** ), określ *nazwa* sekcji. Aby zmienić nazwę sekcji, postępuj zgodnie z *nazwa* znakiem równości (=) i *newname* sekcji.

Ustawianie lub zmienianie sekcji `attributes`, określ przecinek (**,**) następuje jeden lub więcej znaków atrybutów. Aby odwrócić atrybutu, należy poprzedzić jej znakiem wykrzyknika (!). Następujące znaki określić atrybuty pamięci:

|Atrybut|Ustawienie|
|---------------|-------------|
|c|kod|
|d|Discardable|
|e|pliku wykonywalnego|
|mogę|zainicjowana klasa danych|
|k|Pamięć wirtualna|
|m|Usuń łącze|
|o|informacje o łączu|
|p|stronicowana pamięć wirtualna|
|r|przeczytaj|
|s|udostępnione|
|u|niezainicjowanych danych|
|w|pisz|

Do kontroli *wyrównanie*, określić znak **A** następuje jedna z następujących znaków, aby ustawić rozmiar wyrównania w bajtach, w następujący sposób:

|Znak|Wyrównanie rozmiar w bajtach|
|---------------|-----------------------------|
|1|1|
|2|2|
|4|4|
|8|8|
|p|16|
|t|32|
|s|64|
|x|bez wyrównania|

Określ `attributes` i *wyrównanie* znaków w postaci ciągu z żadne inne białe. Znaki nie są z uwzględnieniem wielkości liter.

## <a name="see-also"></a>Zobacz także

[Opcje EDITBIN](editbin-options.md)
