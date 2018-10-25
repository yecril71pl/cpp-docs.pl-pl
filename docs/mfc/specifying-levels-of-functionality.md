---
title: Określanie poziomów funkcjonalności | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CObject class [MFC], adding functionality to derived classes
- runtime [MFC], class information
- serialization [MFC], Cobject
- dynamic creation support
- levels [MFC], functionality in CObject
- run-time class [MFC], information support
- levels [MFC]
ms.assetid: 562669ba-c858-4f66-b5f1-b3beeea4f486
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 765a5293f233cb6df0654416ea2a5463df1095a8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054426"
---
# <a name="specifying-levels-of-functionality"></a>Określanie poziomów funkcjonalności

W tym artykule opisano sposób dodawania następujące poziomy funkcjonalności do Twojej [CObject](../mfc/reference/cobject-class.md)-klasy pochodnej:

- [Informacje o klasie czasu wykonywania](#_core_to_add_run.2d.time_class_information)

- [Obsługa dynamicznego tworzenia](#_core_to_add_dynamic_creation_support)

- [Obsługa serializacji](#_core_to_add_serialization_support)

Aby uzyskać ogólny opis `CObject` funkcji, zapoznaj się z artykułem [wyprowadzanie klasy z obiektu CObject](../mfc/deriving-a-class-from-cobject.md).

- [Informacje o klasie czasu wykonywania](#_core_to_add_run.2d.time_class_information)
#### <a name="_core_to_add_run.2d.time_class_information"></a> Aby dodać informacje o klasie czasu wykonywania

1. Pochodzi z klasy `CObject`, zgodnie z opisem w [wyprowadzanie klasy z obiektu CObject](../mfc/deriving-a-class-from-cobject.md) artykułu.

1. Użyj DECLARE_DYNAMIC — makro w swojej deklaracji klasy, jak pokazano poniżej:

   [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/specifying-levels-of-functionality_1.h)]

1. Użyj IMPLEMENT_DYNAMIC — makro w pliku implementacji (. CPP) klasy. To makro przyjmuje jako argumenty nazwę klasy i jej klasy bazowej, w następujący sposób:

   [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/cpp/specifying-levels-of-functionality_2.cpp)]

> [!NOTE]
>  Zawsze umieszczaj IMPLEMENT_DYNAMIC w pliku implementacji (. CPP) dla swojej klasy. IMPLEMENT_DYNAMIC — makro powinna być oceniana tylko raz podczas kompilacji i w związku z tym nie należy używać w pliku interfejsu (. H) które może potencjalnie być zawarte w więcej niż jeden plik.

#### <a name="_core_to_add_dynamic_creation_support"></a> Aby dodać obsługa dynamicznego tworzenia

1. Pochodzi z klasy `CObject`.

1. Użyj DECLARE_DYNCREATE — makro w deklaracji klasy.

1. Definiowanie konstruktora bez argumentów (Konstruktor).

1. Użyj IMPLEMENT_DYNCREATE — makro w pliku implementacji klasy.

#### <a name="_core_to_add_serialization_support"></a> Aby dodać obsługę serializacji

1. Pochodzi z klasy `CObject`.

1. Zastąp `Serialize` funkcja elementu członkowskiego.

    > [!NOTE]
    >  Jeśli wywołasz `Serialize` bezpośrednio, oznacza to, że nie ma do serializacji obiektu za pomocą wskaźnika polimorficznych, pomiń kroki od 3 do 5.

1. Użyj DECLARE_SERIAL — makro w deklaracji klasy.

1. Definiowanie konstruktora bez argumentów (Konstruktor).

1. Użyj IMPLEMENT_SERIAL — makro w pliku implementacji klasy.

> [!NOTE]
>  "Wskaźnik polimorficznego" wskazuje na obiekt klasy (mu A) lub do obiektu klasy pochodne (np. B). Do serializacji, za pomocą wskaźnika polimorficznych, struktura należy określić klasy środowiska wykonawczego obiektów wykonuje serializację (B), ponieważ może to być obiekt klasy pochodne niektóre klasy bazowej (A).

Aby uzyskać więcej informacji o sposobie włączania serializacji, po utworzeniu klasy pochodnej klasy z `CObject`, zobacz artykuły [pliki w MFC](../mfc/files-in-mfc.md) i [serializacji](../mfc/serialization-in-mfc.md).

## <a name="see-also"></a>Zobacz też

[Wyprowadzanie klasy z obiektu CObject](../mfc/deriving-a-class-from-cobject.md)
