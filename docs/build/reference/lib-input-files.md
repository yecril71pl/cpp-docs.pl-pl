---
title: "Pliki wejściowe LIB | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- Lib
dev_langs:
- C++
helpviewer_keywords:
- input files, LIB
ms.assetid: e1236f0d-cd90-446b-b900-f311f456085c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 5fea7a8700eb2f5a5deee7afd05af8b0de0e4e71
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
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