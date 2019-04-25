---
title: Podstawianie makr
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
ms.openlocfilehash: 43dc9133c53b1c436c0df8c3db66ae8f18604222
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321822"
---
# <a name="macro-substitution"></a>Podstawianie makr

Gdy *makra* zostanie wywołana, każde wystąpienie *ciąg1* definicja ciągu zastępuje *ciąg2*.

## <a name="syntax"></a>Składnia

```
$(macroname:string1=string2)
```

## <a name="remarks"></a>Uwagi

Podstawianie makr jest uwzględniana wielkość liter i jest literałowy; *ciąg1* i *ciąg2* nie można wywołać makra. Podstawienia nie modyfikuje oryginalnej definicji. Można zastąpić tekst w dowolnej wstępnie zdefiniowane makro, z wyjątkiem [ $$@ ](filename-macros.md).

Nie spacje lub tabulatory poprzedzać colon; dowolny po dwukropku są interpretowane jako literał. Jeśli *ciąg2* jest null, wszystkie wystąpienia *ciąg1* są usuwane z ciągu definicji makra.

## <a name="see-also"></a>Zobacz także

[Korzystanie z makro NMAKE](using-an-nmake-macro.md)
