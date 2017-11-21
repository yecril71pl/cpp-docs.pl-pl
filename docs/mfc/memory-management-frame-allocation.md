---
title: "Zarządzanie pamięcią: Ramkę alokacji | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- memory leaks [MFC], frame allocation
- memory [MFC], detecting leaks
- memory [MFC], reclaiming
- memory allocation [MFC], frames
- frame variables [MFC], automatic deletion of
- scope [MFC], frame variables
- heap allocation [MFC], vs. frame allocation
- variables [MFC], frame variables
- memory leaks [MFC], detecting
- memory, releasing [MFC]
- stack frames [MFC]
- memory leaks [MFC], allocating objects on the frame
- detecting memory leaks [MFC]
- frame allocation [MFC]
- frame variables [MFC]
ms.assetid: 945a211a-6f4f-4679-bb6a-b0f2a0d4a6c1
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8a8b0f35874dcf7a51bc2e54045df2c96965b08d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="memory-management-frame-allocation"></a>Zarządzanie pamięcią: alokacja ramek
Podział na ramce przyjmuje nazwy z "ramki stosu", która jest ustawiona zawsze, gdy jest wywoływana funkcja. Ramka stosu jest to obszar pamięci, która tymczasowo przechowuje argumentów do funkcji, a także wszystkie zmienne, które są zdefiniowane lokalne do funkcji. Zmienne ramek są często nazywane zmiennych "Automatyczny", ponieważ kompilator automatycznie przydziela miejsce dla nich.  
  
 Istnieją dwa główne cechy ramkę alokacji. Najpierw podczas definiowania zmiennej lokalnej wystarczającej ilości miejsca jest przydzielona do ramki stosu, aby pomieścić cały zmiennej, nawet jeśli jest dużą tablicę lub struktury danych. Po drugie zmienne ramek są automatycznie usuwane po ich się znaleźć poza zakresem:  
  
 [!code-cpp[NVC_MFC_Utilities#10](../mfc/codesnippet/cpp/memory-management-frame-allocation_1.cpp)]  
  
 Dla zmiennych lokalnych funkcja przypadku wyjścia funkcji, ale zakresu zmiennej ramki może być mniejszy niż funkcji, jeśli używane są zagnieżdżone nawiasy klamrowe odbywa się to przejście zakresu. Ta funkcja automatycznego usuwania zmienne ramek jest bardzo ważne. W przypadku pierwotnych typów prostych (takich jak `int` lub **bajtów**), tablic lub struktury danych automatycznego usuwania po prostu zwraca pamięć używana przez zmienną. Ponieważ zmiennej wykroczyła poza zakres, nie są dostępne w mimo to. W przypadku obiektów języka C++ jednak proces automatycznego usuwania jest nieco bardziej skomplikowane.  
  
 Jeśli obiekt jest zdefiniowana jako zmienną ramki, jego konstruktor jest wywoływana automatycznie w momencie, gdy napotkano definicji. Gdy obiekt poza zakresem, jego destruktora jest wywoływana automatycznie przed jest odzyskać pamięci dla obiektu. To automatyczne konstruowania i zniszczenie może być bardzo przydatne, ale należy uwzględnić automatyczne wywołań, szczególnie w celu destruktor.  
  
 Zaletą Alokacja obiektów w ramce jest, że są automatycznie usuwane. Podczas alokowania obiektów w ramce, nie trzeba martwić zapomniane obiektów, co powoduje przecieki pamięci. (Aby uzyskać szczegółowe informacje na przecieki pamięci, zobacz artykuł [wykrywanie przecieków pamięci w MFC](http://msdn.microsoft.com/en-us/29ee8909-96e9-4246-9332-d3a8aa8d4658).) Wadą Alokacja ramek jest, że zmienne ramek nie można użyć poza ich zakres. Innym czynnikiem, wybierając ramkę alokacji i Alokacja sterty dla dużych struktur i obiektów jest często lepiej użyć sterty zamiast stosu magazynu, ponieważ często wynosi miejsca na stosie.  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią](../mfc/memory-management.md)

