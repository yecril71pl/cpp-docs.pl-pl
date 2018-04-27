---
title: '&lt;limity&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- limits/std::<limits>
- <limits>
dev_langs:
- C++
helpviewer_keywords:
- limits header
ms.assetid: e07d6379-5b00-4a3d-a789-40d41538b59e
caps.latest.revision: 18
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84437f53d8685c842e102fac3da7b062058bb20e
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="ltlimitsgt"></a>&lt;Limity&gt;

Definiuje klasę szablonu `numeric_limits` i wyliczenia dwie liczb zmiennoprzecinkowych oświadczenia dotyczące i zaokrąglania.

## <a name="syntax"></a>Składnia

```cpp
#include <limits>

```

## <a name="remarks"></a>Uwagi

Jawne specjalizacje z `numeric_limits` klasy opisują wiele właściwości typów podstawowych, w tym znaków, liczbą całkowitą i typów zmiennoprzecinkowych i `bool` implementacji zdefiniowana, a nie rozwiązany przez reguły języka C++, które są język. Właściwości opisane w \<limity > obejmują dokładność, minimum i maksimum o rozmiarze reprezentacje zaokrąglania i sygnalizowania błędów typu.

### <a name="enumerations"></a>Wyliczenia

|||
|-|-|
|[float_denorm_style](../standard-library/limits-enums.md#float_denorm_style)|Wyliczenie zawiera opis różnych metod, które można wybrać implementację reprezentujący nieznormalizowany wartość zmiennoprzecinkowa — jeden za mały, aby reprezentować znormalizowaną wartość:|
|[float_round_style](../standard-library/limits-enums.md#float_round_style)|Wyliczenie zawiera opis różnych metod, które można wybrać implementację zaokrąglania wartości zmiennoprzecinkowej na wartość całkowitą.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[numeric_limits, klasa](../standard-library/numeric-limits-class.md)|Klasa szablonu opisuje arytmetyczne właściwości wbudowanych typów wartości liczbowych.|

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
