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
ms.openlocfilehash: f4c01538877d8517cf3394d9e0108ce3a9df2900
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621942"
---
# <a name="deriving-a-class-from-cobject"></a>Wyprowadzanie klasy z obiektu CObject

W tym artykule opisano minimalne kroki niezbędne do wygenerowania klasy z [CObject](reference/cobject-class.md). Inne `CObject` artykuły klasy opisują kroki niezbędne do skorzystania z określonych `CObject` funkcji, takich jak obsługa serializacji i debugowania diagnostycznego.

W dyskusjach dotyczących `CObject` warunków "plik interfejsu" i "plik implementacji" są często używane. Plik interfejsu (często nazywany plikiem nagłówkowym lub. Plik H) zawiera deklarację klasy i inne informacje potrzebne do użycia klasy. Plik implementacji (lub. Plik CPP) zawiera definicję klasy oraz kod implementujący funkcje składowych klasy. Na przykład dla klasy o nazwie `CPerson` można utworzyć plik interfejsu o nazwie Person. H i plik implementacji o nazwie PERSON. CPP. Jednak w przypadku niektórych małych klas, które nie będą współużytkowane przez aplikacje, czasami łatwiej jest połączyć interfejs i implementację w jeden. Plik CPP.

Można wybrać spośród czterech poziomów funkcjonalności podczas wyprowadzania klasy z `CObject` :

- Podstawowe funkcje: brak obsługi informacji o klasie lub serializacji czasu wykonywania, ale obejmuje zarządzanie pamięcią diagnostyczną.

- Podstawowe funkcje Plus obsługa informacji o klasie czasu wykonywania.

- Podstawowe funkcje Plus obsługa informacji o klasie czasu wykonywania i tworzenia dynamicznego.

- Podstawowe funkcje Plus obsługa informacji o klasie czasu wykonywania, tworzenia dynamicznego i serializacji.

Klasy przeznaczone do ponownego użycia (te, które później będą służyć jako klasy bazowe) powinny co najmniej obejmować obsługę klasy w czasie wykonywania i obsługę serializacji, jeśli przewidywane będzie jakiekolwiek przyszłe potrzeby serializacji.

Możesz wybrać poziom funkcjonalności przy użyciu określonych makr deklaracji i implementacji w deklaracji i implementacji klas, z których pochodzą `CObject` .

W poniższej tabeli przedstawiono relacje między makrami używanymi do obsługi serializacji i informacji w czasie wykonywania.

### <a name="macros-used-for-serialization-and-run-time-information"></a>Makra używane do serializacji i informacje w czasie wykonywania

|Użyte makro|CObject:: IsKindOf|CRuntimeClass::<br /><br /> CreateObject|CArchive:: operator>><br /><br /> CArchive:: operator<<|
|----------------|-----------------------|--------------------------------------|-------------------------------------------------------|
|Podstawowe `CObject` funkcje|Nie|Nie|Nie|
|`DECLARE_DYNAMIC`|Yes|Nie|Nie|
|`DECLARE_DYNCREATE`|Tak|Tak|Nie|
|`DECLARE_SERIAL`|Tak|Tak|Tak|

#### <a name="to-use-basic-cobject-functionality"></a>Aby korzystać z podstawowych funkcji CObject

1. Użyj standardowej składni języka C++, aby utworzyć klasę z `CObject` (lub z klasy pochodnej `CObject` ).

   W poniższym przykładzie przedstawiono najprostszy przypadek, pochodny klasy z `CObject` :

   [!code-cpp[NVC_MFCCObjectSample#1](codesnippet/cpp/deriving-a-class-from-cobject_1.h)]

Zwykle jednak może zaistnieć potrzeba przesłonięcia niektórych `CObject` funkcji Członkowskich, aby obsłużyć szczegółowe informacje o nowej klasie. Na przykład można zwykle zastąpić `Dump` funkcję, `CObject` Aby zapewnić dane wyjściowe debugowania dla zawartości klasy. Aby uzyskać szczegółowe informacje na temat przesłonięcia `Dump` , zobacz temat [Dostosowywanie zrzutu obiektów](/previous-versions/visualstudio/visual-studio-2010/sc15kz85(v=vs.100))artykułu. Można również zastąpić `AssertValid` funkcję programu, `CObject` Aby zapewnić dostosowane testy w celu weryfikacji spójności elementów członkowskich danych obiektów klas. Aby uzyskać opis sposobu przesłonięcia `AssertValid` , zobacz [MFC ASSERT_VALID i CObject:: AssertValid](reference/diagnostic-services.md#assert_valid).

W tym artykule opisano [poziomy funkcjonalności](specifying-levels-of-functionality.md) opisujące sposób określania innych poziomów funkcjonalności, w tym informacji o klasie czasu wykonywania, dynamicznego tworzenia obiektów i serializacji.

## <a name="see-also"></a>Zobacz też

[Używanie obiektu CObject](using-cobject.md)
