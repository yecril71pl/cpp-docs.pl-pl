---
title: .CODE
ms.date: 12/06/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 36d9c01d2a24b446ddc91fe73f3cb677067b3e4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987915"
---
# <a name="code-32-bit-masm"></a>. KOD (32-bitowy MASM)

W przypadku użycia z [. MODEL](../../assembler/masm/dot-model.md)wskazuje początek segmentu kodu.

## <a name="syntax"></a>Składnia

> **. KOD** ⟦*Nazwa*⟧

### <a name="parameters"></a>Parametry

\ *nazwy*
Opcjonalny parametr, który określa nazwę segmentu kodu. Domyślna nazwa jest **_TEXT** dla [modeli](../../assembler/masm/dot-model.md)bardzo mały, mały, kompaktowy i płaski. Nazwa domyślna to *modulename*_TEXT dla innych modeli.

## <a name="see-also"></a>Zobacz także

[Dokumentacja dyrektyw](../../assembler/masm/directives-reference.md)\
[.DATA](../../assembler/masm/dot-data.md)
