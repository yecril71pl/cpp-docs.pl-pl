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
ms.openlocfilehash: 02420f2657c7d7d6a7a0294f0321717a3bb2b5d7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786821"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake — Klasa

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>Uwagi

Zapobiega za pomocą operatora `new` w `RuntimeClass`. W związku z tym, należy użyć [funkcji](make-function.md) zamiast tego.

## <a name="members"></a>Elementy członkowskie

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                             | Opis
------------------------------------------------ | ---------------------------------------------------------------------------
[DontUseNewUseMake::operator nowy](#operator-new) | Przeciążenia operatora `new` i zapobiega używana w `RuntimeClass`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`DontUseNewUseMake`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="operator-new"></a>DontUseNewUseMake::operator nowy

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

```cpp
void* operator new(
   size_t,
   _In_ void* placement
);
```

### <a name="parameters"></a>Parametry

*__unnamed0*<br/>
Nienazwany parametr, który określa liczbę bajtów pamięci do przydzielenia.

*placement*<br/>
Typ do przydzielenia.

### <a name="return-value"></a>Wartość zwracana

Zapewnia sposób przekazywania dodatkowych argumentów, jeśli przeciążenia operatora `new`.

### <a name="remarks"></a>Uwagi

Przeciążenia operatora `new` i zapobiega używana w `RuntimeClass`.
