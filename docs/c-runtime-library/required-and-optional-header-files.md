---
title: "Pliki nagłówkowe wymaganych i opcjonalnych | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.headers
dev_langs: C++
helpviewer_keywords:
- include files, required in run time
- header files, required in run time
ms.assetid: f64d0bf5-e2c3-4b42-97d0-443b3d901d9f
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9dde09f2125b595ffb3d79a69b4755353a0116bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="required-and-optional-header-files"></a>Wymagane i opcjonalne nagłówki plików
Opis każdej procedury czasu wykonywania zawiera listę wymaganych i opcjonalnych obejmują, lub nagłówek (. H), pliki dla tej procedury. Pliki nagłówkowe wymagane należy dołączone w celu uzyskania deklaracji funkcji dla procedury lub definicji używany przez inny procedury wywoływana wewnętrznie. Opcjonalne nagłówki plików znajdują się zwykle mógł korzystać z wstępnie zdefiniowanych stałe, definicje typów lub makra w tekście. W poniższej tabeli wymieniono niektóre przykłady opcjonalne nagłówki plików zawartości:  
  
|Definicja|Przykład|  
|----------------|-------------|  
|Definicji makra|Procedury biblioteki jest zaimplementowany jako makra, definicji makra, mogą znajdować się w pliku nagłówka niż pliku nagłówka dla oryginalnego procedury. Na przykład `_toupper` makro jest zdefiniowana w pliku nagłówka CTYPE. H, podczas funkcji `toupper` jest zadeklarowana w STDLIB. H.|  
|Wstępnie zdefiniowane stała|Wiele procedury biblioteki można znaleźć na stałe, które są zdefiniowane w nagłówku plików. Na przykład `_open` procedury używa stałe, takie jak `_O_CREAT`, która jest zdefiniowana w pliku nagłówka FCNTL. H.|  
|Definicja typu|Niektóre procedury biblioteki powrócić, strukturą lub podjąć struktury jako argument. Na przykład procedury we/wy strumienia użyć struktura typu `FILE`, która jest zdefiniowana w stdio —. H.|  
  
 Pliki nagłówka biblioteki wykonawczej Podaj deklaracje funkcji w standardowej stylu zalecane ANSI/ISO C. Kompilator wykonuje sprawdzanie na wszystkich odwołań rutynowych występujący po jego deklaracji funkcji skojarzonego typu. Deklaracje funkcji są szczególnie ważne w przypadku procedury, które zwracają wartości typu innego niż `int`, co jest ustawieniem domyślnym. Procedury, które nie określają ich zwraca wartość w deklaracji będą uznawane za przez kompilator do zwrócenia `int`, co może spowodować nieoczekiwane wyniki. Zobacz [Sprawdzanie typu](../c-runtime-library/type-checking-crt.md) Aby uzyskać więcej informacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka CRT, funkcje](../c-runtime-library/crt-library-features.md)