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
ms.openlocfilehash: 36df93b54accbfdc3ff8f486c41a47af72032c3f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33854613"
---
# <a name="wbufferconvert-class"></a>wbuffer_convert — Klasa

W tym artykule opisano buforu strumienia, który kontroluje przesyłania elementów do i z buforu strumienia bajtów.

## <a name="syntax"></a>Składnia

```cpp
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
 : public std::basic_streambuf<Elem, Traits>
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|`Codecvt`|[Ustawień regionalnych](../standard-library/locale-class.md) aspektu reprezentujący obiekt konwersji.|
|`Elem`|Typ elementu znaków dwubajtowych.|
|`Traits`|Cechy skojarzone z *elementu*.|

## <a name="remarks"></a>Uwagi

Ta klasa szablonu opisuje buforu strumienia, który kontroluje przekazywania elementów typu `_Elem`, którego cech znaków są opisane w klasie `Traits`, do i z buforu strumienia bajtów typu `std::streambuf`.

Konwersja między sekwencji `Elem` wartości i wielobajtowych sekwencji jest wykonywane przez obiekt klasy `Codecvt<Elem, char, std::mbstate_t>`, które spełnia wymagania aspekt konwersja standardowa kodu `std::codecvt<Elem, char, std::mbstate_t>`.

Przechowuje obiekt tej klasy szablonu:

- Wskaźnik do podstawowego buforu strumienia bajtów

- Wskaźnik do obiektu przydzielone konwersji (czyli zwolniony, kiedy [wbuffer_convert —](../standard-library/wbuffer-convert-class.md)
