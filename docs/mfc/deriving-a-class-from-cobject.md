---
title: Wyprowadzanie klasy z obiektu CObject
ms.date: 11/04/2016
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
ms.openlocfilehash: 860af88512acb33ff3035b3a04609165953d80a8
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446974"
---
# <a name="deriving-a-class-from-cobject"></a>Wyprowadzanie klasy z obiektu CObject

W tym artykule opisano minimalne kroki niezbędne do wygenerowania klasy z [CObject](../mfc/reference/cobject-class.md). Inne artykuły klasy `CObject` opisują kroki niezbędne do skorzystania z określonych funkcji `CObject`, takich jak obsługa serializacji i debugowania diagnostycznego.

W dyskusjach `CObject`są często używane terminy "plik interfejsu" i "plik implementacji". Plik interfejsu (często nazywany plikiem nagłówkowym lub. Plik H) zawiera deklarację klasy i inne informacje potrzebne do użycia klasy. Plik implementacji (lub. Plik CPP) zawiera definicję klasy oraz kod implementujący funkcje składowych klasy. Na przykład dla klasy o nazwie `CPerson`zwykle tworzony jest plik interfejsu o nazwie PERSON. H i plik implementacji o nazwie PERSON. CPP. Jednak w przypadku niektórych małych klas, które nie będą współużytkowane przez aplikacje, czasami łatwiej jest połączyć interfejs i implementację w jeden. Plik CPP.

Podczas wyprowadzania klasy z `CObject`można wybrać jedną z czterech poziomów funkcjonalności:

- Podstawowe funkcje: brak obsługi informacji o klasie lub serializacji czasu wykonywania, ale obejmuje zarządzanie pamięcią diagnostyczną.

- Podstawowe funkcje Plus obsługa informacji o klasie czasu wykonywania.

- Podstawowe funkcje Plus obsługa informacji o klasie czasu wykonywania i tworzenia dynamicznego.

- Podstawowe funkcje Plus obsługa informacji o klasie czasu wykonywania, tworzenia dynamicznego i serializacji.

Klasy przeznaczone do ponownego użycia (te, które później będą służyć jako klasy bazowe) powinny co najmniej obejmować obsługę klasy w czasie wykonywania i obsługę serializacji, jeśli przewidywane będzie jakiekolwiek przyszłe potrzeby serializacji.

Możesz wybrać poziom funkcjonalności przy użyciu określonych makr deklaracji i implementacji w deklaracji i implementacji klas, które pochodzą z `CObject`.

W poniższej tabeli przedstawiono relacje między makrami używanymi do obsługi serializacji i informacji w czasie wykonywania.

### <a name="macros-used-for-serialization-and-run-time-information"></a>Makra używane do serializacji i informacje w czasie wykonywania

|Użyte makro|CObject:: IsKindOf|CRuntimeClass::<br /><br /> CreateObject|CArchive:: operator > ><br /><br /> CArchive:: operator < <|
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|
|Podstawowe funkcje `CObject`|Nie|Nie|Nie|
|`DECLARE_DYNAMIC`|Yes|Nie|Nie|
|`DECLARE_DYNCREATE`|Yes|Yes|Nie|
|`DECLARE_SERIAL`|Yes|Yes|Yes|

#### <a name="to-use-basic-cobject-functionality"></a>Aby korzystać z podstawowych funkcji CObject

1. Użyj standardowej C++ składni, aby utworzyć klasę z `CObject` (lub z klasy pochodnej `CObject`).

   W poniższym przykładzie przedstawiono najprostszy przypadek, pochodny klasy z `CObject`:

   [!code-cpp[NVC_MFCCObjectSample#1](../mfc/codesnippet/cpp/deriving-a-class-from-cobject_1.h)]

Zwykle jednak może zaistnieć potrzeba zastąpienia niektórych funkcji elementów członkowskich `CObject`, aby obsłużyć szczegóły nowej klasy. Na przykład zwykle chcesz zastąpić funkcję `Dump` `CObject`, aby zapewnić dane wyjściowe debugowania dla zawartości klasy. Aby uzyskać szczegółowe informacje na temat przesłonięcia `Dump`, zobacz [Dostosowywanie zrzutu obiektów](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100))artykułu. Możesz również zastąpić funkcję `AssertValid` `CObject`, aby zapewnić dostosowany test w celu zweryfikowania spójności elementów członkowskich danych obiektów klas. Opis sposobu przesłonięcia `AssertValid`można znaleźć w temacie [MFC ASSERT_VALID i CObject:: AssertValid](reference/diagnostic-services.md#assert_valid).

W tym artykule opisano [poziomy funkcjonalności](../mfc/specifying-levels-of-functionality.md) opisujące sposób określania innych poziomów funkcjonalności, w tym informacji o klasie czasu wykonywania, dynamicznego tworzenia obiektów i serializacji.

## <a name="see-also"></a>Zobacz też

[Używanie obiektu CObject](../mfc/using-cobject.md)
