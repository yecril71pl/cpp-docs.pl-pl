---
title: Klasa is_trivially_move_assignable | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_move_assignable
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_assignable
ms.assetid: 374f7322-0706-4bc1-a1a5-4191d0315e28
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ee7fb3e92064ebced6390c0eaf81fc68552381ca
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="istriviallymoveassignable-class"></a>is_trivially_move_assignable — klasa

Sprawdza, czy typ ma operator przypisania przenoszenia prosta.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_trivially_move_assignable;
```

### <a name="parameters"></a>Parametry

`Ty` Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu posiada wartość true Jeśli typ `Ty` jest klasa, która ma trivial operator przypisania przenoszenia, w przeciwnym razie posiada wartość false.

Operator przypisania przenoszenia, dla klasy `Ty` jest prosta jeśli:

niejawnie podano

Klasa `Ty` ma żadnych funkcji wirtualnych

Klasa `Ty` ma nie wirtualnych typów podstawowych

klasy wszystkich członków danych niestatycznych typu klasy mają trivial przenoszące operatory przypisania

klasy wszystkich członków danych niestatycznych tablicy typu klasy mają trivial przenoszące operatory przypisania

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
