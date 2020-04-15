---
title: 'Zarządzanie pamięcią: przykłady'
ms.date: 11/04/2016
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
ms.openlocfilehash: 3a1e647175b7b5294e672efbf234e3ae2853e411
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367851"
---
# <a name="memory-management-examples"></a>Zarządzanie pamięcią: przykłady

W tym artykule opisano, jak MFC wykonuje alokacje ramek i alokacji sterty dla każdego z trzech typowych rodzajów alokacji pamięci:

- [Tablica bajtów](#_core_allocation_of_an_array_of_bytes)

- [Struktura danych](#_core_allocation_of_a_data_structure)

- [Obiekt](#_core_allocation_of_an_object)

## <a name="allocation-of-an-array-of-bytes"></a><a name="_core_allocation_of_an_array_of_bytes"></a>Alokacja tablicy bajtów

#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>Aby przydzielić tablicę bajtów w ramce

1. Zdefiniuj tablicę, jak pokazano w poniższym kodzie. Tablica jest automatycznie usuwana, a jej pamięć jest odzyskiwane, gdy zmienna tablicowa kończy działanie jej zakresu.

   [!code-cpp[NVC_MFC_Utilities#1](../mfc/codesnippet/cpp/memory-management-examples_1.cpp)]

#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>Aby przydzielić tablicę bajtów (lub dowolny typ danych pierwotnych) na stercie

1. Użyj **nowego** operatora ze składnią tablicy pokazaną w tym przykładzie:

   [!code-cpp[NVC_MFC_Utilities#2](../mfc/codesnippet/cpp/memory-management-examples_2.cpp)]

#### <a name="to-deallocate-the-arrays-from-the-heap"></a>Aby zdyskwić alokację tablic ze sterty

1. Użyj operatora **usuwania** w następujący sposób:

   [!code-cpp[NVC_MFC_Utilities#3](../mfc/codesnippet/cpp/memory-management-examples_3.cpp)]

## <a name="allocation-of-a-data-structure"></a><a name="_core_allocation_of_a_data_structure"></a>Alokacja struktury danych

#### <a name="to-allocate-a-data-structure-on-the-frame"></a>Aby przydzielić strukturę danych w ramce

1. Zdefiniuj zmienną struktury w następujący sposób:

   [!code-cpp[NVC_MFC_Utilities#4](../mfc/codesnippet/cpp/memory-management-examples_4.cpp)]

   Pamięć zajmowana przez strukturę jest odzyskiwała po zamknięciu jej zakresu.

#### <a name="to-allocate-data-structures-on-the-heap"></a>Aby przydzielić struktury danych na stercie

1. Użyj **nowego,** aby przydzielić struktury danych na stercie i **usunąć,** aby zdyskwalić je, jak pokazano w poniższych przykładach:

   [!code-cpp[NVC_MFC_Utilities#5](../mfc/codesnippet/cpp/memory-management-examples_5.cpp)]

## <a name="allocation-of-an-object"></a><a name="_core_allocation_of_an_object"></a>Alokacja obiektu

#### <a name="to-allocate-an-object-on-the-frame"></a>Aby przydzielić obiekt na ramce

1. Zadeklaruj obiekt w następujący sposób:

   [!code-cpp[NVC_MFC_Utilities#6](../mfc/codesnippet/cpp/memory-management-examples_6.cpp)]

   Destruktor dla obiektu jest wywoływany automatycznie, gdy obiekt kończy działanie jego zakresu.

#### <a name="to-allocate-an-object-on-the-heap"></a>Aby przydzielić obiekt na stercie

1. Użyj **nowego** operatora, który zwraca wskaźnik do obiektu, aby przydzielić obiekty na stosie. Użyj operatora **usuwania,** aby je usunąć.

   Następujące przykłady sterty i ramki zakładają, że `CPerson` konstruktor nie przyjmuje żadnych argumentów.

   [!code-cpp[NVC_MFC_Utilities#7](../mfc/codesnippet/cpp/memory-management-examples_7.cpp)]

   Jeśli argumentem `CPerson` konstruktora jest wskaźnik do **char,** instrukcja alokacji ramki jest:

   [!code-cpp[NVC_MFC_Utilities#8](../mfc/codesnippet/cpp/memory-management-examples_8.cpp)]

   Instrukcja alokacji sterty jest:

   [!code-cpp[NVC_MFC_Utilities#9](../mfc/codesnippet/cpp/memory-management-examples_9.cpp)]

## <a name="see-also"></a>Zobacz też

[Zarządzanie pamięcią: alokacja sterty](../mfc/memory-management-heap-allocation.md)
