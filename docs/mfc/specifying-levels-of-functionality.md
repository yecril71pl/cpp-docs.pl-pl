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
ms.openlocfilehash: f32b9502d2e8bd1c1483d817b759ca204f5c9c1a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="specifying-levels-of-functionality"></a>Określanie poziomów funkcjonalności
W tym artykule opisano sposób dodawania następujące poziomy funkcjonalności do Twojej [CObject](../mfc/reference/cobject-class.md)-klasy:  
  
-   [Informacje o klasie czasu wykonywania](#_core_to_add_run.2d.time_class_information)  
  
-   [Obsługa dynamicznego tworzenia](#_core_to_add_dynamic_creation_support)  
  
-   [Obsługa serializacji](#_core_to_add_serialization_support)  
  
 Ogólny opis `CObject` funkcji, zobacz artykuł [wyprowadzanie klasy z obiektu CObject](../mfc/deriving-a-class-from-cobject.md).  
  
-   [Informacje o klasie czasu wykonywania](#_core_to_add_run.2d.time_class_information)  
#### <a name="_core_to_add_run.2d.time_class_information"></a> Aby dodać informacje o klasie czasu wykonywania  
  
1.  Pochodzi z klasy `CObject`, zgodnie z opisem w [wyprowadzanie klasy z obiektu CObject](../mfc/deriving-a-class-from-cobject.md) artykułu.  
  
2.  Użyj `DECLARE_DYNAMIC` makra w deklaracji klasy, jak pokazano poniżej:  
  
     [!code-cpp[NVC_MFCCObjectSample#2](../mfc/codesnippet/cpp/specifying-levels-of-functionality_1.h)]  
  
3.  Użyj `IMPLEMENT_DYNAMIC` makra w pliku implementacji (. CPP) klasy. To makro przyjmuje jako argumenty nazwę klasy i jej klasa podstawowa w następujący sposób:  
  
     [!code-cpp[NVC_MFCCObjectSample#3](../mfc/codesnippet/cpp/specifying-levels-of-functionality_2.cpp)]  
  
> [!NOTE]
>  Należy zawsze umieszczać `IMPLEMENT_DYNAMIC` w pliku implementacji (. CPP) dla klasy. `IMPLEMENT_DYNAMIC` Makro należy ocenić tylko raz podczas kompilacji i w związku z tym nie należy używać w pliku interfejsu (. H), która może potencjalnie być wchodzące w skład więcej niż jeden plik.  
  
#### <a name="_core_to_add_dynamic_creation_support"></a> Aby dodać obsługa dynamicznego tworzenia  
  
1.  Pochodzi z klasy `CObject`.  
  
2.  Użyj `DECLARE_DYNCREATE` makra w deklaracji klasy.  
  
3.  Zdefiniowanie konstruktora bez argumentów (konstruktora domyślnego).  
  
4.  Użyj `IMPLEMENT_DYNCREATE` makra w pliku implementacji klasy.  
  
#### <a name="_core_to_add_serialization_support"></a> Aby dodać obsługę serializacji  
  
1.  Pochodzi z klasy `CObject`.  
  
2.  Zastąpienie `Serialize` funkcję elementu członkowskiego.  
  
    > [!NOTE]
    >  Jeśli należy wywołać `Serialize` bezpośrednio, oznacza to, że nie chcesz serializacji obiektu za pomocą wskaźnika polimorficznych, pomiń kroki od 3 do 5.  
  
3.  Użyj `DECLARE_SERIAL` makra w deklaracji klasy.  
  
4.  Zdefiniowanie konstruktora bez argumentów (konstruktora domyślnego).  
  
5.  Użyj `IMPLEMENT_SERIAL` makra w pliku implementacji klasy.  
  
> [!NOTE]
>  "Wskaźnik polimorficznym" wskazuje na obiekt klasy (wywołać ją A) lub do obiektu dowolną klasę pochodną (powiedzieć, B). Do serializacji, za pomocą wskaźnika polimorficznych, platformę musi określić klasę środowiska wykonawczego obiektu jest serializacji (B), ponieważ może być obiekt klasy pochodzące z niektórych klasy podstawowej (A).  
  
 Aby uzyskać więcej informacji o sposobie włączania serializacji, jeśli pochodzi z klasy `CObject`, zobacz artykuły [pliki w MFC](../mfc/files-in-mfc.md) i [szeregowanie](../mfc/serialization-in-mfc.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wyprowadzanie klasy z obiektu CObject](../mfc/deriving-a-class-from-cobject.md)
