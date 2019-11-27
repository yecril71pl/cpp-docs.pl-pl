---
title: ALIGN (MASM)
ms.date: 01/02/2019
f1_keywords:
- align
helpviewer_keywords:
- ALIGN directive
ms.assetid: 1c386b23-439f-4ec3-a6de-74427b25e47f
ms.openlocfilehash: 22b18f2e238c780377b84fc2be3eb6678686bb73
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399276"
---
# <a name="align-masm"></a>ALIGN (MASM)

Dyrektywa **align** wyrównuje następny element danych lub instrukcję na adres, który jest wielokrotnością jego parametru. Parametr musi być potęgą liczby 2 (na przykład 1, 2, 4 itd.), która jest mniejsza lub równa wyrównaniu segmentu.

## <a name="syntax"></a>Składnia

> **Wyrównaj** *numer*⟦ ⟧

## <a name="remarks"></a>Uwagi

Dyrektywa **align** pozwala określić początkowe przesunięcie elementu danych lub instrukcji. Wyrównane dane mogą zwiększyć wydajność, kosztem bezstratnego miejsca między elementami danych. Ulepszenia dużej wydajności mogą być widoczne, gdy dostęp do danych znajduje się w granicach, które pasują do wierszy pamięci podręcznej. Dostęp do naturalnych granic dla typów natywnych oznacza krótszy czas poświęcany na wewnętrzną redopasowanie sprzętu włączenia mikrokodu.

Potrzeba wyrównanych instrukcji jest rzadki w nowoczesnych procesorach, które używają prostego modelu adresowania, ale mogą być wymagane w celu przechodzenia w starszym kodzie dla innych modeli adresowania.

Gdy dane są wyrównane, pominięte miejsce jest uzupełnione zerami. Gdy instrukcje są wyrównane, pominięte miejsce jest wypełniane odpowiednio NOP instrukcjami.

## <a name="see-also"></a>Zobacz także

[Nawet](even.md)\
[Dokumentacja dyrektyw](directives-reference.md)
