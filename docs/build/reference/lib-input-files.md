---
title: Pliki wyjściowe LIB
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: 648871464dbc99972b8ca40579046347727e81cf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269391"
---
# <a name="lib-input-files"></a>Pliki wyjściowe LIB

Pliki wejściowe, oczekiwany przez LIB zależą od trybu, w którym jest on używany, jak pokazano w poniższej tabeli.

|Tryb|Dane wejściowe|
|----------|-----------|
|Domyślne (Tworzenie lub modyfikowanie biblioteki)|Pliki obiektowych (.obj) COFF, bibliotekami COFF (lib), 32-bitowych plików obiektu (.obj) Format modelu obiektu (OMF)|
|Wyodrębnianie do członka za pomocą/extract|COFF biblioteki (lib)|
|Tworzenie eksportu pliku i zaimportować biblioteki z/DEF|Plik definicji modułu (.def), plikach obiektowych (.obj) COFF, bibliotekami COFF (lib), plikach obiektowych (.obj) OMF 32-bitowy|

> [!NOTE]
>  Biblioteki OMF utworzone przez 16-bitową wersję biblioteki nie można użyć jako dane wejściowe do 32-bitowej wersji LIB.

## <a name="see-also"></a>Zobacz także

[Informacje o LIB](overview-of-lib.md)
