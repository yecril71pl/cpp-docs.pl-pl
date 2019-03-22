---
title: Wyprowadzanie klasy z obiektu CObject
ms.date: 11/04/2016
f1_keywords:
- CObject
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
ms.openlocfilehash: 26fdab5165ca098c5d7813ebf44983c261094449
ms.sourcegitcommit: c1f646c8b72f330fa8cf5ddb0f8f261ba10d16f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/21/2019
ms.locfileid: "58328444"
---
# <a name="deriving-a-class-from-cobject"></a>Wyprowadzanie klasy z obiektu CObject

W tym artykule opisano minimalną procedurę niezbędną do wyprowadzenia klasy z [CObject](../mfc/reference/cobject-class.md). Inne `CObject` artykuły klasy opisują czynności, aby móc korzystać z określonych `CObject` funkcje, takie jak serializacji i diagnostycznych obsługę debugowania.

W omówieniach dotyczących `CObject`, warunki interfejsu "pliku" i "plik implementacji" są często używane. Plik interfejsu (często nazywany plik nagłówkowy lub. Plik H) zawiera deklarację klasy i innych informacji potrzebnych do korzystania z tej klasy. Plik implementacji (lub). Plik CPP) zawiera definicji klasy, a także kod, który implementuje funkcje składowych klasy. Na przykład dla klasy o nazwie `CPerson`, zazwyczaj należy utworzyć plik interfejs o nazwie osoby. Godz. i pliku z implementacją o nazwie osoby. CPP. Jednak dla niektórych małych klas, które nie będą udostępniane między aplikacjami, czasami jest łatwiej łączyć interfejsu i implementacji w jednym. Plik CPP.

Można wybierać spośród czterech poziomów funkcjonalności podczas wyprowadzania z klasy `CObject`:

- Podstawowe funkcje: Brak obsługi informacji o klasie czasu wykonywania lub serializacji ale obejmuje zarządzanie pamięcią diagnostycznych.

- Podstawowe funkcje oraz wsparcie dla informacji o klasie czasu wykonywania.

- Podstawowe funkcje oraz wsparcie dla informacji o klasie czasu wykonywania dynamiczne tworzenie.

- Podstawowe funkcje oraz wsparcie dla informacji o klasie czasu wykonywania, dynamiczne tworzenie i serializacji.

Klasy przeznaczone do ponownego wykorzystania (te, które później będą służyć jako klay bazowe) zawiera co najmniej obsługę klasy środowiska wykonawczego i serializacji, jeśli przewidywanego na potrzeby przyszłych serializacji.

Wybierz poziom funkcjonalności przy użyciu określonych deklarację i implementację makr w deklarację i implementację klasy pochodzić od `CObject`.

W poniższej tabeli przedstawiono relacje między makra używane do obsługi serializacji i informacje o czasie wykonywania.

### <a name="macros-used-for-serialization-and-run-time-information"></a>Makra używane w ramach serializacji i informacji czasu wykonywania

|Makra używane|CObject::IsKindOf|CRuntimeClass::<br /><br /> CreateObject|CArchive::operator >><br /><br /> CArchive::operator <<|
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|
|Podstawowe `CObject` funkcji|Nie|Nie|Nie|
|`DECLARE_DYNAMIC`|Yes|Nie|Nie|
|`DECLARE_DYNCREATE`|Yes|Yes|Nie|
|`DECLARE_SERIAL`|Yes|Yes|Tak|

#### <a name="to-use-basic-cobject-functionality"></a>Aby korzystać z podstawowych funkcji CObject

1. Użyj normalnej składni języka C++ do wyprowadzenia klasy z `CObject` (lub z klasy pochodzącej od `CObject`).

   W poniższym przykładzie pokazano najprostszym przypadku wyprowadzenia klasy z `CObject`:

   [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/cpp/deriving-a-class-from-cobject_1.h)]

Zwykle jednak możesz zastąpić niektóre `CObject`przez funkcje składowe w celu obsługi szczegółowe informacje na temat nowej klasie. Na przykład zazwyczaj warto zastąpić `Dump` funkcji `CObject` zapewnienie dane wyjściowe debugowania zawartość swojej klasy. Aby uzyskać szczegółowe informacje o zastępowaniu `Dump`, zapoznaj się z artykułem [Dostosowywanie zrzutu obiektu](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100)). Możesz także Przesłoń `AssertValid` funkcji `CObject` zapewnienie dostosowane testowania w celu zweryfikowania spójności składowych danych klas obiektów. Opis sposobu zastąpienia `AssertValid`, zobacz [MFC ASSERT_VALID i CObject::AssertValid](reference/diagnostic-services.md#assert_valid).

Artykuł [Określanie poziomów funkcjonalności](../mfc/specifying-levels-of-functionality.md) opisuje sposób określenia innych poziomach funkcjonalności, w tym informacje o klasie czasu wykonywania, dynamiczne tworzenie obiektów i serializacji.

## <a name="see-also"></a>Zobacz także

[Używanie obiektu CObject](../mfc/using-cobject.md)
