---
title: 'Zarządzanie pamięcią: Przykłady | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], memory allocation
- data structures [MFC]
- arrays [MFC], allocating resources
- objects [MFC], allocating memory
- data structures [MFC], allocating memory
- examples [MFC], memory allocation
- heap allocation [MFC], examples
- memory allocation [MFC], arrays
- MFC, memory management
- struct memory allocation [MFC]
- types [MFC], memory allocation
- memory allocation [MFC], objects
- memory allocation [MFC], examples
- arrays [MFC], memory management
- frame allocation [MFC]
- memory allocation [MFC], data structures
ms.assetid: f10240f8-b698-4c83-9288-97a54318930b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21efd095a1d8e89c140ef39072a753c300a3043b
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929310"
---
# <a name="memory-management-examples"></a>Zarządzanie pamięcią: przykłady
W tym artykule opisano, jak MFC wykonuje ramkę alokacji i Alokacje sterty dla każdego z trzech typów typowych alokacji pamięci:  
  
-   [Tablica bajtów](#_core_allocation_of_an_array_of_bytes)  
  
-   [Struktury danych](#_core_allocation_of_a_data_structure)  
  
-   [Obiekt](#_core_allocation_of_an_object)  
  
##  <a name="_core_allocation_of_an_array_of_bytes"></a> Alokacja tablicy bajtów  
  
#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>Aby przydzielić tablicy bajtów w ramce  
  
1.  Zdefiniuj tablicy, jak pokazano w następującym kodem. Tablica jest automatycznie usuwana i jego pamięci odzyskana, gdy zmienna tablicy jest kończona jej zakres.  
  
     [!code-cpp[NVC_MFC_Utilities#1](../mfc/codesnippet/cpp/memory-management-examples_1.cpp)]  
  
#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>Aby przydzielić tablicy bajtów (lub dowolny typ danych pierwotnych) na stercie  
  
1.  Użyj **nowe** operator przy użyciu składni tablicy w poniższym przykładzie:  
  
     [!code-cpp[NVC_MFC_Utilities#2](../mfc/codesnippet/cpp/memory-management-examples_2.cpp)]  
  
#### <a name="to-deallocate-the-arrays-from-the-heap"></a>Aby zwolnić tablice sterty  
  
1.  Użyj **usunąć** operatora w następujący sposób:  
  
     [!code-cpp[NVC_MFC_Utilities#3](../mfc/codesnippet/cpp/memory-management-examples_3.cpp)]  
  
##  <a name="_core_allocation_of_a_data_structure"></a> Alokacja struktury danych  
  
#### <a name="to-allocate-a-data-structure-on-the-frame"></a>Aby przydzielić strukturą danych w ramce  
  
1.  Zdefiniuj zmienną struktury w następujący sposób:  
  
     [!code-cpp[NVC_MFC_Utilities#4](../mfc/codesnippet/cpp/memory-management-examples_4.cpp)]  
  
     Pamięć zajmowane przez strukturę jest odzyskana po wydaniu jej zakres.  
  
#### <a name="to-allocate-data-structures-on-the-heap"></a>Aby przydzielić struktur danych na stercie  
  
1.  Użyj **nowe** przydzielić struktur danych na stosie i **usunąć** można cofnąć alokacji, jak pokazano w poniższych przykładach:  
  
     [!code-cpp[NVC_MFC_Utilities#5](../mfc/codesnippet/cpp/memory-management-examples_5.cpp)]  
  
##  <a name="_core_allocation_of_an_object"></a> Alokacja obiektów  
  
#### <a name="to-allocate-an-object-on-the-frame"></a>Aby przydzielić obiektu w ramce  
  
1.  Deklarowanie obiektu w następujący sposób:  
  
     [!code-cpp[NVC_MFC_Utilities#6](../mfc/codesnippet/cpp/memory-management-examples_6.cpp)]  
  
     Destruktor dla obiekt jest wywoływana automatycznie, gdy obiekt opuszcza jej zakres.  
  
#### <a name="to-allocate-an-object-on-the-heap"></a>Aby przydzielić obiektu na stercie  
  
1.  Użyj **nowe** operatora, który zwraca wskaźnik do obiektu, aby przydzielić obiektów na stercie. Użyj **usunąć** operatora, aby je usunąć.  
  
     W poniższych przykładach sterty i ramki przyjęto założenie, że `CPerson` Konstruktor nie przyjmuje żadnych argumentów.  
  
     [!code-cpp[NVC_MFC_Utilities#7](../mfc/codesnippet/cpp/memory-management-examples_7.cpp)]  
  
     Jeśli argument `CPerson` Konstruktor jest wskaźnik do **char**, instrukcja dla Alokacja ramek jest:  
  
     [!code-cpp[NVC_MFC_Utilities#8](../mfc/codesnippet/cpp/memory-management-examples_8.cpp)]  
  
     Instrukcja alokacji sterty jest:  
  
     [!code-cpp[NVC_MFC_Utilities#9](../mfc/codesnippet/cpp/memory-management-examples_9.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie pamięcią: alokacja sterty](../mfc/memory-management-heap-allocation.md)

