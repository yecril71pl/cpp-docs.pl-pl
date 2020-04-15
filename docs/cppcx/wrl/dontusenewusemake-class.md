---
title: DontUseNewUseMake — Klasa
ms.date: 09/21/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
helpviewer_keywords:
- Microsoft::WRL::Details::DontUseNewUseMake class
- Microsoft::WRL::Details::DontUseNewUseMake::operator new operator
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
ms.openlocfilehash: ae67373b4f2f2d4a199b939b06e6f526f1365446
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371551"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake — Klasa

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

## <a name="syntax"></a>Składnia

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>Uwagi

Zapobiega używaniu `new` `RuntimeClass`operatora w pliku . W związku z tym należy użyć [Make funkcji](make-function.md) zamiast tego.

## <a name="members"></a>Elementy członkowskie

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                             | Opis
------------------------------------------------ | ---------------------------------------------------------------------------
[DontUseNewUseMake::operator nowy](#operator-new) | Przeciąża `new` operatora i zapobiega jego `RuntimeClass`użyciu w .

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`DontUseNewUseMake`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Obszar nazw:** Microsoft::WRL::Dszczegóły

## <a name="dontusenewusemakeoperator-new"></a><a name="operator-new"></a>DontUseNewUseMake::operator nowy

Obsługuje infrastrukturę WRL i nie jest przeznaczony do użycia bezpośrednio z kodu.

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>Parametry

*__unnamed0*<br/>
Nienazwany parametr, który określa liczbę bajtów pamięci do przydzielenia.

*Umieszczenie*<br/>
Typ, który ma zostać przydzielony.

### <a name="return-value"></a>Wartość zwracana

Umożliwia przekazywanie dodatkowych argumentów w `new`przypadku przeciążenia operatora .

### <a name="remarks"></a>Uwagi

Przeciąża `new` operatora i zapobiega jego `RuntimeClass`użyciu w .
