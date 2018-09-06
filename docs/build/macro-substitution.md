---
title: Podstawianie makr | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, macro substitution
- macros, NMAKE
- substitution macros in NMAKE
ms.assetid: 47465cfe-fd92-49db-aebe-7c2d7ecceb73
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f71ef2e1a8f337a4cd415169b6f9d817042f19a
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894398"
---
# <a name="macro-substitution"></a>Podstawianie makr

Gdy *makra* zostanie wywołana, każde wystąpienie *ciąg1* definicja ciągu zastępuje *ciąg2*.

## <a name="syntax"></a>Składnia

```
$(macroname:string1=string2)
```

## <a name="remarks"></a>Uwagi

Podstawianie makr jest uwzględniana wielkość liter i jest literałowy; *ciąg1* i *ciąg2* nie można wywołać makra. Podstawienia nie modyfikuje oryginalnej definicji. Można zastąpić tekst w dowolnej wstępnie zdefiniowane makro, z wyjątkiem [ $$@ ](../build/filename-macros.md).

Nie spacje lub tabulatory poprzedzać colon; dowolny po dwukropku są interpretowane jako literał. Jeśli *ciąg2* jest null, wszystkie wystąpienia *ciąg1* są usuwane z ciągu definicji makra.

## <a name="see-also"></a>Zobacz też

[Korzystanie z makro NMAKE](../build/using-an-nmake-macro.md)