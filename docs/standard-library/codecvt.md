---
title: '&lt;codecvt —&gt; | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- codecvt
- <codecvt>
dev_langs:
- C++
helpviewer_keywords:
- codecvt header
ms.assetid: d44ee229-00d5-4761-9b48-0c702122789d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5d4e07c4869bd345e77f0af4f30f694773aed114
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845144"
---
# <a name="ltcodecvtgt"></a>&lt;codecvt&gt;

Definiuje kilka klasy szablonu, które opisują obiekty na podstawie szablonu klasy [codecvt](../standard-library/codecvt-class.md). Te obiekty mogą służyć jako [aspekty ustawień regionalnych](../standard-library/locale-class.md#facet_class) umożliwiające sterowanie konwersje między sekwencję wartości typu `Elem` i sekwencję wartości typu `char`.

## <a name="syntax"></a>Składnia

```cpp
#include <codecvt>

```

## <a name="remarks"></a>Uwagi

Aspekty ustawień regionalnych zadeklarowany w nagłówku tej konwersji między kilka kodowanie znaków. Znaki dwubajtowe (przechowywane w programie w ustalonym rozmiarze liczb całkowitych):

- UCS 4 są zakodowane w Unicode (ISO 10646) w programie jako liczba całkowita 32-bitowych.

- UCS-2 jest Unicode zakodowane w programie jako 16-bitową liczbę całkowitą.

- UTF-16 jest Unicode w programie został zakodowany jako jedna lub dwie 16-bitowych liczb całkowitych. (Należy pamiętać, że nie spełnia wszystkie wymagania prawidłowym kodowaniem znaków dwubajtowych standardowe C lub C++ standardowa. Niemniej jednak jest powszechnie używany jako takie.)

Dla strumienie bajtów (przechowywane w pliku przekazywane w kolejności bajtów i przechowywane w programie w tablicy `char`):

- UTF-8 to Unicode kodowane w ramach strumień bajtów jako jeden lub więcej bajtów 8 bitowych z kolejnością bajtów deterministyczna.

- UTF-16LE jest zakodowany w strumieniu bajtów jako UTF-16 Unicode z każdego 16-bitową liczbę całkowitą, najpierw widoczne jako dwa bajty 8 bitowych, mniej znaczący bajt.

- UTF-16BE jest zakodowany w strumieniu bajtów jako UTF-16 Unicode z każdego 16-bitową liczbę całkowitą, najpierw widoczne jako dwa bajty 8 bitowych, bardziej znaczący bajt.

### <a name="enumerations"></a>Wyliczenia

|||
|-|-|
|[codecvt_mode](../standard-library/codecvt-enums.md#codecvt_mode)|Zawiera informacje o konfiguracji dla ustawień regionalnych aspektami.|

### <a name="classes"></a>Klasy

|Class|Opis|
|-|-|
|[codecvt_utf8](codecvt-utf8-class.md)|Reprezentuje aspektu ustawień regionalnych, który wykonuje konwersję między znaki dwubajtowe zakodowane jako UCS 2 lub UCS 4 i strumień bajtów zakodowane jako UTF-8.|
|[codecvt_utf8_utf16](codecvt-utf8-utf16-class.md)|Reprezentuje aspektu ustawień regionalnych, który wykonuje konwersję między znaki dwubajtowe zakodowane jako UTF-16, a strumień bajtów zakodowane jako UTF-8.|
|[codecvt_utf16](codecvt-utf16-class.md)|Reprezentuje aspektu ustawień regionalnych, który wykonuje konwersję między znaki dwubajtowe zakodowane jako UCS 2 lub UCS 4 i strumień bajtów zakodowane jako UTF-16LE lub UTF-16BE.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<codecvt >

**Namespace:** stdt

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
