---
title: DontUseNewUseMake::operator nowy Operator | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::DontUseNewUseMake::operator new
dev_langs:
- C++
helpviewer_keywords:
- operator new operator
ms.assetid: 6af07a0d-2271-430c-9d9b-5a4223fed049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 99e82de06f64816521c47c78648108a9ae815279
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46443231"
---
# <a name="dontusenewusemakeoperator-new-operator"></a>DontUseNewUseMake::operator nowy operator

Obsługuje infrastrukturę biblioteki WRL i nie jest przeznaczona do użycia bezpośrednio w kodzie.

## <a name="syntax"></a>Składnia

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

## <a name="return-value"></a>Wartość zwracana

Zapewnia sposób przekazywania dodatkowych argumentów, jeśli przeciążenia operatora **nowe**.

## <a name="remarks"></a>Uwagi

Przeciążenia operatora **nowe** i zapobiega używana w `RuntimeClass`.

## <a name="requirements"></a>Wymagania

**Nagłówek:** implements.h

**Namespace:** Microsoft::wrl:: details

## <a name="see-also"></a>Zobacz też

[DontUseNewUseMake, klasa](../windows/dontusenewusemake-class.md)<br/>
[Microsoft::WRL::Details, przestrzeń nazw](../windows/microsoft-wrl-details-namespace.md)