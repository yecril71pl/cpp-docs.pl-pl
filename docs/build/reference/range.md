---
title: /RANGE
ms.date: 11/04/2016
f1_keywords:
- /RANGE
helpviewer_keywords:
- /RANGE dumpbin option
- -RANGE dumpbin option
ms.assetid: 7eeba266-32be-49cc-a350-96bdf541f98a
ms.openlocfilehash: c631057e47e1a52a58d2b1304133dfdfc008ae14
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319710"
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

## <a name="see-also"></a>Zobacz także

[Opcje DUMPBIN](dumpbin-options.md)
