---
title: Określanie poziomów funkcjonalności
ms.date: 11/06/2018
helpviewer_keywords:
- CObject class [MFC], adding functionality to derived classes
- runtime [MFC], class information
- serialization [MFC], Cobject
- dynamic creation support
- levels [MFC], functionality in CObject
- run-time class [MFC], information support
- levels [MFC]
ms.assetid: 562669ba-c858-4f66-b5f1-b3beeea4f486
ms.openlocfilehash: c3b4ecb38054748f36d75ca43e32d6447d3d2428
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307292"
---
# <a name="specifying-levels-of-functionality"></a>Określanie poziomów funkcjonalności

W tym artykule opisano sposób dodawania następujące poziomy funkcjonalności do Twojej [CObject](../mfc/reference/cobject-class.md)-klasy pochodnej:

- Informacje o klasie czasu wykonywania

- Obsługa dynamicznego tworzenia

- Obsługa serializacji

Aby uzyskać ogólny opis `CObject` funkcji, zapoznaj się z artykułem [wyprowadzanie klasy z obiektu CObject](../mfc/deriving-a-class-from-cobject.md).

## <a name="to-add-run-time-class-information"></a>Aby dodać informacje o klasie czasu wykonywania

1. Pochodzi z klasy `CObject`, zgodnie z opisem w [wyprowadzanie klasy z obiektu CObject](../mfc/deriving-a-class-from-cobject.md) artykułu.

1. Użyj DECLARE_DYNAMIC — makro w swojej deklaracji klasy, jak pokazano poniżej:

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/specifying-levels-of-functionality_1.h)]

1. Użyj IMPLEMENT_DYNAMIC — makro w pliku implementacji (. CPP) klasy. To makro przyjmuje jako argumenty nazwę klasy i jej klasy bazowej, w następujący sposób:

   [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/cpp/specifying-levels-of-functionality_2.cpp)]

> [!NOTE]
> Zawsze umieszczaj IMPLEMENT_DYNAMIC w pliku implementacji (. CPP) dla swojej klasy. IMPLEMENT_DYNAMIC — makro powinna być oceniana tylko raz podczas kompilacji i w związku z tym nie należy używać w pliku interfejsu (. H) które może potencjalnie być zawarte w więcej niż jeden plik.

## <a name="to-add-dynamic-creation-support"></a>Aby dodać obsługa dynamicznego tworzenia

1. Pochodzi z klasy `CObject`.

1. Użyj DECLARE_DYNCREATE — makro w deklaracji klasy.

1. Definiowanie konstruktora bez argumentów (Konstruktor).

1. Użyj IMPLEMENT_DYNCREATE — makro w pliku implementacji klasy.

## <a name="to-add-serialization-support"></a>Aby dodać obsługę serializacji

1. Pochodzi z klasy `CObject`.

1. Zastąp `Serialize` funkcja elementu członkowskiego.

   > [!NOTE]
   > Jeśli wywołasz `Serialize` bezpośrednio, oznacza to, że nie ma do serializacji obiektu za pomocą wskaźnika polimorficznych, pomiń kroki od 3 do 5.

1. Użyj DECLARE_SERIAL — makro w deklaracji klasy.

1. Definiowanie konstruktora bez argumentów (Konstruktor).

1. Użyj IMPLEMENT_SERIAL — makro w pliku implementacji klasy.

> [!NOTE]
> "Wskaźnik polimorficznego" wskazuje na obiekt klasy (mu A) lub do obiektu klasy pochodne (np. B). Do serializacji, za pomocą wskaźnika polimorficznych, struktura należy określić klasy środowiska wykonawczego obiektów wykonuje serializację (B), ponieważ może to być obiekt klasy pochodne niektóre klasy bazowej (A).

Aby uzyskać więcej informacji o sposobie włączania serializacji, po utworzeniu klasy pochodnej klasy z `CObject`, zobacz artykuły [pliki w MFC](../mfc/files-in-mfc.md) i [serializacji](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Zobacz także

[Wyprowadzanie klasy z obiektu CObject](../mfc/deriving-a-class-from-cobject.md)
