---
title: -ZAKRESU | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /RANGE
dev_langs:
- C++
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 47e7525b8c1872616182141d624bff8f94571952
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712195"
---
# <a name="range"></a>/RANGE

Modyfikuje dane wyjściowe polecenia dumpbin, gdy jest używana z innymi opcjami dumpbin, takie jak /RAWDATA lub /DISASM.

## <a name="syntax"></a>Składnia

```
/RANGE:vaMin[,vaMax]
```

## <a name="parameters"></a>Parametry

*vaMin*<br/>
Wirtualny adres ma operacji dumpbin, aby rozpocząć.

*vaMax*<br/>
(Opcjonalnie) Wirtualny adres ma operacji dumpbin, aby zakończyć. Jeśli nie zostanie określony, dumpbin zaczną się na końcu pliku.

## <a name="remarks"></a>Uwagi

Aby wyświetlić wirtualne adresy obrazu, należy użyć pliku mapy obrazu (adres RVA + podstawowa), **/DISASM** lub **/HEADERS** — opcja polecenia dumpbin lub okna dezasemblacji w debugerze programu Visual Studio.

## <a name="example"></a>Przykład

W tym przykładzie **/zakresu** jest używane do modyfikowania wyświetlanie **/disasm** opcji. W tym przykładzie wartością początkową jest wyrażona jako liczba dziesiętna, a wartość końcowa jest określony jako liczba szesnastkowa.

```
dumpbin /disasm /range:4219334,0x004061CD t.exe
```

## <a name="see-also"></a>Zobacz też

[Opcje DUMPBIN](../../build/reference/dumpbin-options.md)