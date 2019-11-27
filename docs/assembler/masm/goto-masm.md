---
title: GOTO (MASM)
ms.date: 08/30/2018
f1_keywords:
- goto
helpviewer_keywords:
- GOTO directive
ms.assetid: 6a5f73e7-6784-4eae-ac52-4fc77a7f369f
ms.openlocfilehash: 424ff295fe37e7c5ff02897a01b99a7c75876f85
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397484"
---
# <a name="goto-masm"></a>GOTO (MASM)

Przenosi zestaw do wiersza oznaczonego **:** _macrolabel_.

## <a name="syntax"></a>Składnia

> **Przejdź** do *macrolabel*

## <a name="remarks"></a>Uwagi

**Polecenie goto** jest dozwolone tylko wewnątrz [makra](macro.md), [dla](for-masm.md), [FORC](forc.md), [REPEAT](repeat.md)i [while](while-masm.md) . Wartość docelowa *macrolabel* musi być jedyną dyrektywą w wierszu i musi być poprzedzona znakiem dwukropka.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](directives-reference.md)
