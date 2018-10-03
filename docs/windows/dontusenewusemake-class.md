---
title: Dontusenewusemake — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 09/21/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
dev_langs:
- C++
helpviewer_keywords:
- Microsoft::WRL::Details::DontUseNewUseMake class
- Microsoft::WRL::Details::DontUseNewUseMake::operator new operator
ms.assetid: 8b38d07b-fc14-4cea-afb9-4c1a7dde0093
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9c1f3a57401a3ab2efd45cab2dace127010c24e6
ms.sourcegitcommit: 1d9bd38cacbc783fccd3884b7b92062161c91c84
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2018
ms.locfileid: "48235285"
---
# <a name="dontusenewusemake-class"></a>DontUseNewUseMake — Klasa

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

```cpp
class DontUseNewUseMake;
```

## <a name="remarks"></a>Uwagi

Zapobiega za pomocą operatora `new` w `RuntimeClass`. W związku z tym, należy użyć [funkcji](../windows/make-function.md) zamiast tego.

## <a name="members"></a>Elementy członkowskie

### <a name="public-operators"></a>Operatory publiczne

Nazwa                                             | Opis
------------------------------------------------ | ---------------------------------------------------------------------------
[DontUseNewUseMake::operator nowy](#operator-new) | Przeciążenia operatora `new` i zapobiega używana w `RuntimeClass`.

## <a name="inheritance-hierarchy"></a>Hierarchia dziedziczenia

`DontUseNewUseMake`

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

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
