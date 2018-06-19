---
title: Wyprowadzanie klasy z obiektu CObject | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CObject
dev_langs:
- C++
helpviewer_keywords:
- DECLARE_DYNCREATE macro [MFC]
- DECLARE_SERIAL macro [MFC]
- macros [MFC], serialization
- serialization [MFC], macros
- DECLARE_DYNAMIC macro [MFC]
- derived classes [MFC], from CObject
- CObject class [MFC], deriving serializable classes
- CObject class [MFC], deriving from
ms.assetid: 5ea4ea41-08b5-4bd8-b247-c5de8c152a27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2d0b629617c1592387f3f959996fd3e9837242ea
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349360"
---
# <a name="deriving-a-class-from-cobject"></a>Wyprowadzanie klasy z obiektu CObject
W tym artykule opisano minimalną kroki niezbędne do wyprowadzenia klasy z [CObject](../mfc/reference/cobject-class.md). Inne `CObject` klasy artykuły zawierają czynności, aby móc korzystać z określonych `CObject` funkcje, takie jak serializacji i diagnostycznych obsługę debugowania.  
  
 W dyskusjach `CObject`, warunki "plik interfejsu" i "pliku implementacji" są często używane. Plik interfejsu (często nazywane pliku nagłówka lub. Plik H) zawiera deklaracji klasy i inne informacje potrzebne do użycia klasy. Plik implementacji (lub. Pliku CPP) zawiera definicji klasy, a także kod, który implementuje funkcje Członkowskie klas. Na przykład dla klasy o nazwie `CPerson`, zazwyczaj należy utworzyć plik interfejs o nazwie osoby. H i pliku z implementacją o nazwie osoby. CPP. Jednak dla niektórych małych klas, które nie będą udostępniane między aplikacjami, czasami jest łatwiej łączyć interfejsu i wdrożenia w ramach jednej. Pliku CPP.  
  
 Można wybierać spośród czterech poziomów funkcjonalności podczas tworzenia klasy pochodnej z klasy `CObject`:  
  
-   Podstawowe funkcje: nie obsługuje informacje o klasie czasu wykonywania lub serializacji ale obejmuje zarządzanie pamięcią diagnostycznych.  
  
-   Podstawowe funkcje oraz pomocy technicznej, aby uzyskać informacje o klasie czasu wykonywania.  
  
-   Podstawowe funkcje oraz obsługę informacji o klasie czasu wykonywania i tworzenie dynamiczne.  
  
-   Podstawowe funkcje oraz obsługę informacji o klasie czasu wykonywania, tworzenie dynamicznych i serializacji.  
  
 Klasy przeznaczone do ponownego użycia (te, które później będzie służyć jako klasy podstawowe) zawiera co najmniej klasie czasu wykonywania obsługi i pomocy technicznej serializacji, jeśli przewiduje się potrzeby przyszłych serializacji.  
  
 Wybierz poziom funkcjonalności przy użyciu określonych deklaracji i implementacji makra w deklaracji i stosowania pochodzi od klasy `CObject`.  
  
 W poniższej tabeli przedstawiono relacje między makra używane do obsługi serializacji i informacje czasu wykonywania.  
  
### <a name="macros-used-for-serialization-and-run-time-information"></a>Makra używany do serializacji i informacje czasu wykonywania  
  
|Makra używane|CObject::IsKindOf|CRuntimeClass::<br /><br /> CreateObject|CArchive::operator >><br /><br /> CArchive::operator <<|  
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|  
|Podstawowe `CObject` funkcji|Nie|Nie|Nie|  
|`DECLARE_DYNAMIC`|Tak|Nie|Nie|  
|`DECLARE_DYNCREATE`|Tak|Tak|Nie|  
|`DECLARE_SERIAL`|Tak|Tak|Tak|  
  
#### <a name="to-use-basic-cobject-functionality"></a>Podstawowa funkcja CObject  
  
1.  Użyj normalnej składni języka C++ wyprowadzenia klasy z `CObject` (lub z klasy pochodzącej od `CObject`).  
  
     W poniższym przykładzie przedstawiono najprostszym przypadku wyprowadzenia klasy z `CObject`:  
  
     [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/cpp/deriving-a-class-from-cobject_1.h)]  
  
 Zwykle, jednak może zajść potrzeba zastępowania niektórych `CObject`w funkcji elementów członkowskich do obsługi szczegółowe informacje na temat nowej klasy. Na przykład, zwykle można zastąpić `Dump` funkcji `CObject` zapewnienie danych wyjściowych debugowania dla zawartości klasy. Aby uzyskać szczegółowe informacje o zastępowaniu `Dump`, zapoznaj się z artykułem [diagnostyki: zrzucanie zawartość obiektu](http://msdn.microsoft.com/en-us/727855b1-5a83-44bd-9fe3-f1d535584b59). Można również zastąpić `AssertValid` funkcji `CObject` zapewnienie testowania niestandardowych w celu zweryfikowania spójności danych członków klasy obiektów. Opis sposobu zastąpienia `AssertValid`, zobacz [assert_valid — MFC i CObject::AssertValid](http://msdn.microsoft.com/en-us/7654fb75-9e9a-499a-8165-0a96faf2d5e6).  
  
 Artykuł [Określanie poziomów funkcjonalności](../mfc/specifying-levels-of-functionality.md) opisuje sposób określenia innych poziomach funkcjonalności, w tym informacje o klasie czasu wykonywania, dynamiczne tworzenie obiektów i serializacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie obiektu CObject](../mfc/using-cobject.md)

