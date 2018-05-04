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
ms.openlocfilehash: 140a0f1d9ef6fdb3ca5e6d6977804684c88af1fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="lib-input-files"></a>Pliki wyjściowe LIB
Pliki wejściowe oczekiwany przez LIB zależą od tryb, w którym jest on używany, jak pokazano w poniższej tabeli.  
  
|Tryb|Dane wejściowe|  
|----------|-----------|  
|Domyślne (Tworzenie lub modyfikowanie biblioteki)|COFF, pliki obiektu (.obj), bibliotekami COFF (lib), 32-bitowe pliki obiektu (.obj) Format modelu obiektu (OMF)|  
|Wyodrębnianie członka o/extract|Biblioteka COFF (lib)|  
|Tworzenie eksportu pliku i zaimportować biblioteki z/DEF|Plik definicji modułu (.def), COFF, pliki obiektu (.obj), bibliotekami COFF (lib), 32-bitowe pliki obiektu (.obj) OMF|  
  
> [!NOTE]
>  Biblioteki OMF utworzone przez 16-bitową wersję LIB nie może służyć jako dane wejściowe do 32-bitowej wersji LIB.  
  
## <a name="see-also"></a>Zobacz też  
 [Informacje o LIB](../../build/reference/overview-of-lib.md)