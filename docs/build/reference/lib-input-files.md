---
title: Pliki wejściowe LIB | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 952c3345234192e3798fea483d527cd3afec4bff
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702471"
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

## <a name="see-also"></a>Zobacz też

[Informacje o LIB](../../build/reference/overview-of-lib.md)