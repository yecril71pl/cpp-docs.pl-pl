---
title: /SECTION (EDITBIN)
ms.date: 11/04/2016
f1_keywords:
- /section_editbin
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
ms.openlocfilehash: 770e1d1c1cf288a7fe68f5bd076791d43f5b8572
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438915"
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)

```
/SECTION:name[=newname][,attributes][alignment]
```

## <a name="remarks"></a>Uwagi

Ta opcja zmienia atrybuty sekcji, zastępując atrybuty ustawione, gdy plik obiektu dla sekcji został skompilowany lub połączony.

Po dwukropku ( **:** ) Określ *nazwę* sekcji. Aby zmienić nazwę sekcji, należy użyć *nazwy* z znakiem równości (=) i *nowa_nazwa* dla sekcji.

Aby ustawić lub zmienić `attributes`sekcji, określ przecinek ( **,** ), po którym następuje jeden lub więcej atrybutów znaków. Aby Negate atrybut, poprzedź go znakiem wykrzyknika (!). Następujące znaki określają atrybuty pamięci:

|Atrybut|Ustawienie|
|---------------|-------------|
|c|kod|
|d|Odrzucanie|
|e|plik|
|mogę|zainicjowane dane|
|K|buforowana pamięć wirtualna|
|m|Usuwanie linku|
|o|Informacje o linku|
|p|stronicowana pamięć wirtualna|
|r|przeczytaj|
|s|udostępnione|
|u|Niezainicjowane dane|
|w|pisz|

Aby kontrolować *wyrównanie*, określ znak **a** , po którym następuje jeden z następujących znaków, aby ustawić rozmiar wyrównania w bajtach w następujący sposób:

|Znak|Rozmiar wyrównania w bajtach|
|---------------|-----------------------------|
|1|1|
|2|2|
|4|4|
|8|8|
|p|16|
|t|32|
|s|64|
|x|bez wyrównania|

Określ `attributes` i *wyrównania* jako ciąg bez białych znaków. W znakach nie jest rozróżniana wielkość liter.

## <a name="see-also"></a>Zobacz też

[Opcje EDITBIN](editbin-options.md)
