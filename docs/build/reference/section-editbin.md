---
title: -SECTION (EDITBIN) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /section
dev_langs:
- C++
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f91d467681d5a4d5bf4eaa5f042ef44b87810b3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701990"
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
|K|Pamięć wirtualna|
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

## <a name="see-also"></a>Zobacz też

[Opcje EDITBIN](../../build/reference/editbin-options.md)