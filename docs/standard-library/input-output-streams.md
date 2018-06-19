---
title: Strumienie wyjściowe dane wejściowe | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- I/O [C++], stream
- stream I/O
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 51a7a9aff4f77444bbec46a9739fae91cac3c104
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33845934"
---
# <a name="inputoutput-streams"></a>Input/Output Streams

`basic_iostream`, która jest zdefiniowana w pliku nagłówka \<istream >, jest szablon klasy obiektów, które obsługiwać oba wejściowa i wyjściowa opartego na znakach strumieni We/Wy.

Istnieją dwie definicje typów definiujące specjalizacjach specyficzne dla znaku `basic_iostream` i może pomóc zwiększyć czytelność kodu: `iostream` (nie należy mylić z plikiem nagłówka \<iostream >) jest to strumień we/wy na podstawie `basic_iostream<char>`; `wiostream` jest to strumień we/wy na podstawie `basic_iostream<wchar_t>`.

Aby uzyskać więcej informacji, zobacz [basic_iostream — klasa](../standard-library/basic-iostream-class.md), [iostream](../standard-library/basic-iostream-class.md), i [wiostream](../standard-library/basic-iostream-class.md).

Wynikających z `basic_iostream` jest szablon klasy `basic_fstream`, które są używane do strumienia danych znakowych do i z plików.

Istnieją również definicje typów dostarczające specjalizacjach specyficzne dla znaku `basic_fstream`. Są one `fstream`, który jest strumień we/wy pliku, który jest oparty na `char`, i `wfstream`, który jest oparty na strumieniu we/wy pliku `wchar_t`. Aby uzyskać więcej informacji, zobacz [basic_fstream — klasa](../standard-library/basic-fstream-class.md), [fstream —](../standard-library/basic-fstream-class.md), i [wfstream](../standard-library/basic-fstream-class.md). Przy użyciu tych definicje typów wymaga włączenia nagłówka pliku \<fstream — >.

> [!NOTE]
> Gdy `basic_fstream` obiekt jest używany do wykonywania operacji We/Wy pliku, bufor źródłowy zawiera oddzielnie wyznaczony pozycji do odczytu i zapisu, bieżących danych wejściowych i bieżącego położenia dane wyjściowe są również powiązane ze sobą i w związku z tym przenosi odczytu niektórych danych pozycja danych wyjściowych.

Szablon klasy `basic_stringstream` i jego typowe specjalizacji `stringstream`, są często używane do pracy z obiektami strumień we/wy do wstawienia i wyodrębniania danych znakowych. Aby uzyskać więcej informacji, zobacz [basic_stringstream — klasa](../standard-library/basic-stringstream-class.md).

## <a name="see-also"></a>Zobacz także

[stringstream](../standard-library/basic-stringstream-class.md)<br/>
[basic_stringstream, klasa](../standard-library/basic-stringstream-class.md)<br/>
[\<sstream — >](../standard-library/sstream.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)<br/>
