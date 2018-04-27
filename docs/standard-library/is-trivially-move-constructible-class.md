---
title: Klasa is_trivially_move_constructible | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- type_traits/std::is_trivially_move_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_trivially_move_constructible
ms.assetid: 740bdec7-65e5-47b3-b94f-a2479ceac3ec
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 58bcd000f34941ec37141f9be4b4b3a56e0b9197
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="istriviallymoveconstructible-class"></a>is_trivially_move_constructible — klasa

Testy, jeśli typ ma trivial przenoszenie konstruktora.

## <a name="syntax"></a>Składnia

```cpp
template <class Ty>
struct is_trivially_move_constructible;
```

### <a name="parameters"></a>Parametry

`Ty` Typ do zapytania.

## <a name="remarks"></a>Uwagi

Wystąpienie typu predykatu posiada wartość true Jeśli typ `Ty` jest klasa, która ma Konstruktor przenoszący trivial w inny sposób przechowuje wartość false.

Przenoszenie konstruktora dla klasy `Ty` jest prosta jeśli:

został niejawnie zadeklarowany.

jego typy parametrów są odpowiadające niejawne deklaracji

Klasa `Ty` ma żadnych funkcji wirtualnych

Klasa `Ty` ma nie wirtualnych typów podstawowych

Klasa nie ma żadnych członków danych niestatycznych nietrwałe

wszystkie bezpośrednio podstawowych klasy `Ty` mieć konstruktorów przenoszenia prosta

klasy wszystkich członków danych niestatycznych typu klasy mają konstruktorów przenoszenia prosta

klasy wszystkich członków danych niestatycznych tablicy typu klasy mają konstruktorów przenoszenia prosta

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<type_traits >

**Namespace:** Standard

## <a name="see-also"></a>Zobacz także

[<type_traits>](../standard-library/type-traits.md)<br/>
