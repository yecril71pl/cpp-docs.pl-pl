---
title: Określanie nazwy ścieżki
ms.date: 11/04/2016
helpviewer_keywords:
- names [C++], compiler output files
- cl.exe compiler, output files
- output files, specifying pathnames
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
ms.openlocfilehash: dcff3610255c40f4e06201e52a53eb5dd965a4be
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62317942"
---
# <a name="specifying-the-pathname"></a>Określanie nazwy ścieżki

Każda opcja pliku wyjściowego przyjmuje *pathname* argument, który można określić lokalizację i nazwę pliku wyjściowego. Argument może zawierać nazwę dysku, katalogu i nazwa pliku. Nie może być spacji między opcją a argumentem.

Jeśli *pathname* zawiera nazwę pliku bez rozszerzenia, kompilator zapewnia dane wyjściowe rozszerzenia domyślnego. Jeśli *pathname* zawiera katalog, ale nie nazwę pliku, kompilator tworzy plik o domyślnej nazwie w określonym katalogu. Nazwa domyślna jest oparta na Nazwa podstawowa pliku źródłowego i domyślnym rozszerzeniem, na podstawie typu pliku wyjściowego. Jeśli pozostawisz *pathname* całkowicie, kompilator tworzy plik z nazwą domyślną w domyślnym katalogu.

Alternatywnie *pathname* argument może być nazwą urządzenia (AUX, CON, PRN lub NUL), a nie nazwę pliku. Nie używaj spacji między opcję i nazwę urządzenia lub dwukropek jako część nazwy urządzenia.

|Nazwa urządzenia|Reprezentuje|
|-----------------|----------------|
|AUX|Urządzenie pomocnicze|
|CON|Konsola|
|PRN|Drukarki|
|NUL|Urządzenie o wartości null (nie utworzony plik)|

## <a name="example"></a>Przykład

Następujące polecenie w wierszu pliku mapowania są wysyłane do drukarki:

```
CL /FmPRN HELLO.CPP
```

## <a name="see-also"></a>Zobacz także

[Plik wyjściowy (/F), opcje](output-file-f-options.md)<br/>
[Opcje kompilatora MSVC](compiler-options.md)<br/>
[Składnia wiersza polecenia kompilatora MSVC](compiler-command-line-syntax.md)
