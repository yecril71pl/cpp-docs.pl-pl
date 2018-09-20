---
title: Określanie nazwy ścieżki | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- names [C++], compiler output files
- cl.exe compiler, output files
- output files, specifying pathnames
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 636326e5af577b4e26c61a2094fe73dd4a680f2d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46402476"
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

## <a name="see-also"></a>Zobacz też

[Plik wyjściowy (/F), opcje](../../build/reference/output-file-f-options.md)<br/>
[Opcje kompilatora](../../build/reference/compiler-options.md)<br/>
[Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)