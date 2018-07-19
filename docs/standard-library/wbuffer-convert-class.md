---
title: wbuffer_convert — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
dev_langs:
- C++
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 364ae6c544f58f09208cefeec9d3984de35120e1
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965219"
---
# <a name="wbufferconvert-class"></a>wbuffer_convert — Klasa

W tym artykule opisano buforu strumieni, który kontroluje przekazywanie elementów do i z buforu strumienia bajtów.

## <a name="syntax"></a>Składnia

```cpp
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
 : public std::basic_streambuf<Elem, Traits>
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*codecvt —*|[Ustawień regionalnych](../standard-library/locale-class.md) reguł, który reprezentuje obiekt konwersji.|
|*Elem*|Typ elementu znaków dwubajtowych.|
|*Cechy*|Cechy skojarzone z *Elem*.|

## <a name="remarks"></a>Uwagi

Ta klasa szablonu opisuje buforu strumieni, który kontroluje transmisji elementów typu `_Elem`, którego cech są opisane przez klasę `Traits`, do i z typu bufor strumienia bajtów `std::streambuf`.

Konwersja między sekwencjami `Elem` wartości i wielobajtowych sekwencji jest wykonywana przez obiekt klasy `Codecvt<Elem, char, std::mbstate_t>`, które spełnia wymagania aspekt standardowych konwersji kodu `std::codecvt<Elem, char, std::mbstate_t>`.

Przechowuje obiekt tej klasy szablonu:

- Wskaźnik do podstawowego buforu strumienia bajtów

- Wskaźnik do obiektu przydzielonego konwersji (który jest zwolniony, kiedy [wbuffer_convert —](../standard-library/wbuffer-convert-class.md)
