---
title: 'Zarządzanie pamięcią: Przykłady'
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
ms.openlocfilehash: 5ed50bfba03f29fdd16e6f615b193109656f3ce6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62352167"
---
# <a name="memory-management-examples"></a>Zarządzanie pamięcią: Przykłady

W tym artykule opisano, jak MFC wykonuje ramkę alokacji i Alokacje sterty dla każdego z trzech typowe rodzaje alokacji pamięci:

- [Tablica bajtów](#_core_allocation_of_an_array_of_bytes)

- [Struktura danych](#_core_allocation_of_a_data_structure)

- [Obiekt](#_core_allocation_of_an_object)

##  <a name="_core_allocation_of_an_array_of_bytes"></a> Alokacja tablicę bajtów

#### <a name="to-allocate-an-array-of-bytes-on-the-frame"></a>Do przydzielania tablicy bajtów na ramce

1. Należy zdefiniować tablicę, jak pokazano w następującym kodem. Tablica jest automatycznie usuwana, a swojej pamięci odzyskana, gdy zmienną tablicy kończy działanie w swoim zakresie.

   [!code-cpp[NVC_MFC_Utilities#1](../mfc/codesnippet/cpp/memory-management-examples_1.cpp)]

#### <a name="to-allocate-an-array-of-bytes-or-any-primitive-data-type-on-the-heap"></a>Aby przydzielić tablicy bajtów (lub dowolnego typu danych pierwotnych) na stosie

1. Użyj **nowe** operator za pomocą składni tablicy w poniższym przykładzie:

   [!code-cpp[NVC_MFC_Utilities#2](../mfc/codesnippet/cpp/memory-management-examples_2.cpp)]

#### <a name="to-deallocate-the-arrays-from-the-heap"></a>Można cofnąć alokacji tablic ze sterty

1. Użyj **Usuń** operatora w następujący sposób:

   [!code-cpp[NVC_MFC_Utilities#3](../mfc/codesnippet/cpp/memory-management-examples_3.cpp)]

##  <a name="_core_allocation_of_a_data_structure"></a> Alokacja struktury danych

#### <a name="to-allocate-a-data-structure-on-the-frame"></a>Aby przydzielić to struktura danych na ramce

1. Zdefiniuj zmiennej struktury w następujący sposób:

   [!code-cpp[NVC_MFC_Utilities#4](../mfc/codesnippet/cpp/memory-management-examples_4.cpp)]

   Pamięć zajęta przez strukturę jest odzyskana, gdy jej zakres kończy działanie.

#### <a name="to-allocate-data-structures-on-the-heap"></a>Aby przydzielić struktur danych na stosie

1. Użyj **nowe** przydzielić struktur danych na stosie i **Usuń** można cofnąć alokacji, jak pokazano w poniższych przykładach:

   [!code-cpp[NVC_MFC_Utilities#5](../mfc/codesnippet/cpp/memory-management-examples_5.cpp)]

##  <a name="_core_allocation_of_an_object"></a> Alokacja obiektu

#### <a name="to-allocate-an-object-on-the-frame"></a>Aby przydzielić obiektu w ramce

1. Zadeklaruj obiektu w następujący sposób:

   [!code-cpp[NVC_MFC_Utilities#6](../mfc/codesnippet/cpp/memory-management-examples_6.cpp)]

   Destruktor obiektu automatycznie jest wywoływane, gdy obiekt kończy działanie w swoim zakresie.

#### <a name="to-allocate-an-object-on-the-heap"></a>Można przydzielić obiektu na stercie

1. Użyj **nowe** operatora, który zwraca wskaźnik do obiektu, do alokowania obiektów na stosie. Użyj **Usuń** operatora, aby je usunąć.

   W poniższych przykładach sterty i ramki przyjęto założenie, że `CPerson` Konstruktor nie przyjmuje żadnych argumentów.

   [!code-cpp[NVC_MFC_Utilities#7](../mfc/codesnippet/cpp/memory-management-examples_7.cpp)]

   Jeśli argument `CPerson` Konstruktor jest wskaźnikiem do **char**, zestawienie za Alokacja ramek:

   [!code-cpp[NVC_MFC_Utilities#8](../mfc/codesnippet/cpp/memory-management-examples_8.cpp)]

   Instrukcja dla alokacji sterty jest:

   [!code-cpp[NVC_MFC_Utilities#9](../mfc/codesnippet/cpp/memory-management-examples_9.cpp)]

## <a name="see-also"></a>Zobacz także

[Zarządzanie pamięcią: alokacja sterty](../mfc/memory-management-heap-allocation.md)
