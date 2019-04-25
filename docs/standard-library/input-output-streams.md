---
title: Strumienie wejście wyjście
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], stream
- stream I/O
ms.assetid: 21a97566-91a7-42d6-b2f8-a4c16bc926f1
ms.openlocfilehash: d426baacb52095ab2d933263fdac8e312fc29558
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62159239"
---
# <a name="inputoutput-streams"></a>Input/Output Streams

`basic_iostream`, która została zdefiniowana w pliku nagłówkowym \<istream >, jest szablonem klasy, dla obiektów, które obsługiwać oba modele danych wejściowych i wyjściowych opartego na znakach strumieniach we/wy.

Istnieją dwie definicje typów, które definiują specyficzne dla znaków specjalizacje `basic_iostream` i mogą pomóc poprawić czytelność kodu: `iostream` (nie należy mylić z plikiem nagłówka \<iostream >) jest strumień we/wy, który jest oparty na `basic_iostream<char>`; `wiostream` jest strumień we/wy, który jest oparty na `basic_iostream<wchar_t>`.

Aby uzyskać więcej informacji, zobacz [basic_iostream — klasa](../standard-library/basic-iostream-class.md), [iostream](../standard-library/basic-iostream-class.md), i [wiostream](../standard-library/basic-iostream-class.md).

Wynikających ze `basic_iostream` jest szablonem klasy `basic_fstream`, który jest używany do strumienia znaków danych do i z plików.

Istnieją również definicje typów, zapewniające specjalizacje znaków specyficznych `basic_fstream`. Są one `fstream`, czyli strumień we/wy pliku, który jest oparty na **char**, i `wfstream`, czyli strumień we/wy pliku, który jest oparty na **wchar_t**. Aby uzyskać więcej informacji, zobacz [basic_fstream — klasa](../standard-library/basic-fstream-class.md), [fstream —](../standard-library/basic-fstream-class.md), i [wfstream](../standard-library/basic-fstream-class.md). Korzystanie z tych definicji typów wymaga włączenia plik nagłówkowy \<fstream — >.

> [!NOTE]
> Gdy `basic_fstream` obiekt jest używany do wykonywania operacji We/Wy w pliku, mimo że podstawowego buforu zawiera oddzielnie wyznaczony pozycji do odczytu i zapisu, bieżących danych wejściowych i bieżącej pozycji dane wyjściowe są powiązane ze sobą i w związku z tym, przenosi odczytu niektórych danych Pozycja w danych wyjściowych.

Szablon klasy `basic_stringstream` i jego typowe specjalizacji `stringstream`, są często używane do pracy z obiektami strumienia we/wy do wstawiania i wyodrębnianie danych znakowych. Aby uzyskać więcej informacji, zobacz [basic_stringstream — klasa](../standard-library/basic-stringstream-class.md).

## <a name="see-also"></a>Zobacz także

[stringstream](../standard-library/basic-stringstream-class.md)<br/>
[basic_stringstream, klasa](../standard-library/basic-stringstream-class.md)<br/>
[\<sstream>](../standard-library/sstream.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)<br/>
