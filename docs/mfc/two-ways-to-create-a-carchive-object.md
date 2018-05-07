---
title: Dwa sposoby tworzenia obiektu CArchive | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CArchive
dev_langs:
- C++
helpviewer_keywords:
- CArchive class [MFC], closing CArchive objects
- CArchive objects [MFC], closing
- I/O [MFC], creating CArchive objects
- serialization [MFC], CArchive class
- CArchive objects [MFC]
- storage [MFC], CArchive class [MFC]
- data storage [MFC], CArchive class
- CArchive class [MFC], constructor
ms.assetid: aefa28ce-b55c-40dc-9e42-5f038030985d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 87abaa5a3564c61a6944e0cc31e81375f92a3a80
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="two-ways-to-create-a-carchive-object"></a>Dwa sposoby tworzenia obiektu CArchive
Istnieją dwa sposoby tworzenia `CArchive` obiektu:  
  
-   [Niejawne Tworzenie obiektu CArchive przez platformę](#_core_implicit_creation_of_a_carchive_object_via_the_framework)  
  
-   [Jawne utworzenie obiektu CArchive](#_core_explicit_creation_of_a_carchive_object)  
  
##  <a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a> Niejawne Tworzenie obiektu CArchive przez platformę  
 Najbardziej typowe i najłatwiejszy, sposób jest umożliwienie framework utworzyć `CArchive` obiektu dokumentu w imieniu Zapisz, Zapisz jako i polecenia Otwórz w menu Plik.  
  
 Oto, co platformę nie w przypadku użytkowników aplikacji wydaje polecenia Zapisz jako z menu Plik:  
  
1.  Przedstawia informacje o **Zapisz jako** okno dialogowe i pobiera nazwy pliku od użytkownika.  
  
2.  Otwiera plik o nazwie przez użytkownika jako `CFile` obiektu.  
  
3.  Tworzy `CArchive` obiekt, który wskazuje na to `CFile` obiektu. Podczas tworzenia `CArchive` obiektu, w ramach Ustawia tryb na "store" (zapisu, serializować), a nie "obciążenia" (Odczyt, deserializacji).  
  
4.  Wywołania `Serialize` funkcji zdefiniowanej w Twojej **CDocument**-klasy przekazanie jej przez odwołanie do `CArchive` obiektu.  
  
 W dokumencie `Serialize` funkcja następnie zapisuje dane do `CArchive` obiektu, zgodnie z objaśnieniem wkrótce. Po powrocie z Twojej `Serialize` niszczy platformę funkcji `CArchive` obiektu, a następnie `CFile` obiektu.  
  
 W związku z tym jeśli umożliwisz framework utworzyć `CArchive` obiekt do dokumentu, wszystkie wystarczy wykonać to implementacja tego dokumentu `Serialize` funkcja, która zapisuje i odczytuje do i z archiwum. Masz również implementować `Serialize` dla każdego `CObject`— pochodnych obiektów który dokumentu `Serialize` funkcji z kolei serializuje bezpośrednio lub pośrednio.  
  
##  <a name="_core_explicit_creation_of_a_carchive_object"></a> Jawne utworzenie obiektu CArchive  
 Oprócz serializacji dokumentu przez platformę, są tylko gdy może być konieczne `CArchive` obiektu. Na przykład można serializować danych ze Schowka reprezentowany przez `CSharedFile` obiektu. Możesz też użyć interfejsu użytkownika do zapisania pliku, który jest inny niż oferowany przez platformę. W takim przypadku można jawnie utworzyć `CArchive` obiektu. W tym ten sam sposób, w ramach nie, korzystając z następującej procedury.  
  
#### <a name="to-explicitly-create-a-carchive-object"></a>Aby jawnie tworzenia obiektu CArchive  
  
1.  Utworzyć `CFile` lub obiektu pochodną `CFile`.  
  
2.  Przekaż `CFile` obiekt do konstruktora dla `CArchive`, jak pokazano w poniższym przykładzie:  
  
     [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]  
  
     Drugi argument `CArchive` Konstruktor jest wyliczany określający czy archiwum będą używane do przechowywania lub ładowania danych do lub z pliku. `Serialize` Funkcji obiektu ten stan sprawdza, wywołując `IsStoring` funkcji dla obiektu archiwum.  
  
 Po zakończeniu przechowywanie i ładowanie danych do lub z `CArchive` obiektów, zamknij go. Mimo że `CArchive` (i `CFile`) obiektów zostanie automatycznie zamknięte archiwum (i plik), jest dobrym rozwiązaniem jawne żądanie, ponieważ ułatwia odzyskiwanie z błędami. Aby uzyskać więcej informacji na temat obsługi błędów, zobacz artykuł [wyjątki: wyjątki połowowe i usuwania](../mfc/exceptions-catching-and-deleting-exceptions.md).  
  
#### <a name="to-close-the-carchive-object"></a>Aby zamknąć obiektu CArchive  
  
1.  Poniższy przykład przedstawia sposób zamknąć `CArchive` obiektu:  
  
     [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja: serializacja obiektu](../mfc/serialization-serializing-an-object.md)

