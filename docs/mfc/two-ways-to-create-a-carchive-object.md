---
title: Dwa sposoby tworzenia obiektu CArchive
ms.date: 11/04/2016
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
ms.openlocfilehash: 71592584d4ecdd3169ad894861a97fa668c04ee8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370955"
---
# <a name="two-ways-to-create-a-carchive-object"></a>Dwa sposoby tworzenia obiektu CArchive

Istnieją dwa sposoby `CArchive` tworzenia obiektu:

- [Niejawne tworzenie CArchive obiektu za pośrednictwem struktury](#_core_implicit_creation_of_a_carchive_object_via_the_framework)

- [Jawne tworzenie obiektu CArchive](#_core_explicit_creation_of_a_carchive_object)

## <a name="implicit-creation-of-a-carchive-object-via-the-framework"></a><a name="_core_implicit_creation_of_a_carchive_object_via_the_framework"></a>Niejawne tworzenie CArchive Object za pośrednictwem struktury

Najczęstszym i najprostszym sposobem jest umożliwienie framework `CArchive` tworzenia obiektu dla dokumentu w imieniu polecenia Zapisz, Zapisz jako i Otwórz w menu Plik.

Oto, co robi struktura, gdy użytkownik aplikacji wydaje polecenie Zapisz jako z menu Plik:

1. Przedstawia okno dialogowe **Zapisz jako** i pobiera nazwę pliku od użytkownika.

1. Otwiera plik nazwany przez użytkownika `CFile` jako obiekt.

1. Tworzy `CArchive` obiekt, który `CFile` wskazuje na ten obiekt. Podczas tworzenia `CArchive` obiektu, ramach ustawia tryb "store" (zapis, serializacji), w przeciwieństwie do "load" (read, deserialize).

1. Wywołuje `Serialize` funkcję zdefiniowaną `CDocument`w klasie pochodnej, przekazując `CArchive` jej odwołanie do obiektu.

`Serialize` Funkcja dokumentu następnie zapisuje dane `CArchive` do obiektu, jak wyjaśniono wkrótce. Po powrocie `Serialize` z funkcji, ramach `CArchive` niszczy obiekt, a następnie `CFile` obiekt.

W związku z tym jeśli `CArchive` pozwolisz struktury utworzyć obiekt dla dokumentu, wszystko `Serialize` co musisz zrobić, to zaimplementować funkcję dokumentu, który zapisuje i odczytuje do i z archiwum. Należy również zaimplementować `Serialize` dla wszystkich `CObject`obiektów `Serialize` pochodnych, które funkcja dokumentu z kolei serializuje bezpośrednio lub pośrednio.

## <a name="explicit-creation-of-a-carchive-object"></a><a name="_core_explicit_creation_of_a_carchive_object"></a>Jawne tworzenie obiektu CArchive

Oprócz serializacji dokumentu za pośrednictwem struktury, istnieją inne sytuacje, gdy może być potrzebny `CArchive` obiekt. Na przykład można serializować dane do i ze Schowka, reprezentowane przez `CSharedFile` obiekt. Lub można użyć interfejsu użytkownika do zapisywania pliku, który różni się od tego oferowanego przez strukturę. W takim przypadku można jawnie `CArchive` utworzyć obiekt. Można to zrobić w taki sam sposób, jak struktura, przy użyciu poniższej procedury.

#### <a name="to-explicitly-create-a-carchive-object"></a>Aby jawnie utworzyć CArchive obiektu

1. Konstruuj `CFile` obiekt lub `CFile`obiekt pochodzący z pliku .

1. Przekaż `CFile` obiekt do konstruktora dla `CArchive`, jak pokazano w poniższym przykładzie:

   [!code-cpp[NVC_MFCSerialization#5](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_1.cpp)]

   Drugi argument `CArchive` do konstruktora jest wyliczona wartość, która określa, czy archiwum będzie używany do przechowywania lub ładowania danych do lub z pliku. Funkcja `Serialize` obiektu sprawdza ten stan, `IsStoring` wywołując funkcję obiektu archiwum.

Po zakończeniu przechowywania lub ładowania danych do `CArchive` lub z obiektu, zamknij go. Chociaż `CArchive` (i) `CFile`obiekty automatycznie zamkną archiwum (i plik), dobrą praktyką jest jawnie to zrobić, ponieważ ułatwia odzyskiwanie z błędów. Aby uzyskać więcej informacji na temat obsługi błędów, zobacz artykuł [Wyjątki: Przechwytywanie i usuwanie wyjątków](../mfc/exceptions-catching-and-deleting-exceptions.md).

#### <a name="to-close-the-carchive-object"></a>Aby zamknąć CArchive obiektu

1. Poniższy przykład ilustruje `CArchive` sposób zamknięcia obiektu:

   [!code-cpp[NVC_MFCSerialization#6](../mfc/codesnippet/cpp/two-ways-to-create-a-carchive-object_2.cpp)]

## <a name="see-also"></a>Zobacz też

[Serializacja: serializacja obiektu](../mfc/serialization-serializing-an-object.md)
