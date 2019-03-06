---
title: Pliki wyjściowe LIB
ms.date: 11/04/2016
f1_keywords:
- Lib
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
ms.openlocfilehash: fb0095bd9e8699fbc9a1a144833d12d2cf4a1f83
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423095"
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

[Informacje o LIB](../../build/reference/overview-of-lib.md)
