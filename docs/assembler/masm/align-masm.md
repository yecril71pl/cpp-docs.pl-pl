---
title: ALIGN (MASM)
ms.date: 12/17/2019
f1_keywords:
- align
helpviewer_keywords:
- ALIGN directive
ms.assetid: 1c386b23-439f-4ec3-a6de-74427b25e47f
ms.openlocfilehash: 700721768deaf92e88b32a97e68c6e017219d19d
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316593"
---
# <a name="align"></a>ALIGN

Dyrektywa **align** wyrównuje następny element danych lub instrukcję na adres, który jest wielokrotnością jego parametru. Parametr musi być potęgą liczby 2 (na przykład 1, 2, 4 itd.), która jest mniejsza lub równa wyrównaniu segmentu.

## <a name="syntax"></a>Składnia

> **Wyrównaj** ⟦*constantExpression*⟧

## <a name="remarks"></a>Uwagi

Dyrektywa **align** pozwala określić początkowe przesunięcie elementu danych lub instrukcji. Wyrównane dane mogą zwiększyć wydajność, kosztem bezstratnego miejsca między elementami danych. Ulepszenia dużej wydajności mogą być widoczne, gdy dostęp do danych znajduje się w granicach, które pasują do wierszy pamięci podręcznej. Dostęp do naturalnych granic dla typów natywnych oznacza krótszy czas poświęcany na wewnętrzną redopasowanie sprzętu włączenia mikrokodu.

Potrzeba wyrównanych instrukcji jest rzadki w nowoczesnych procesorach, które używają prostego modelu adresowania, ale mogą być wymagane w celu przechodzenia w starszym kodzie dla innych modeli adresowania.

Gdy dane są wyrównane, pominięte miejsce jest uzupełnione zerami. Gdy instrukcje są wyrównane, pominięte miejsce jest wypełniane odpowiednio NOP instrukcjami.

## <a name="see-also"></a>Zobacz także

[Nawet](even.md)\
[Dokumentacja dyrektyw](directives-reference.md)\
[MASM BNF, gramatyka](masm-bnf-grammar.md)
