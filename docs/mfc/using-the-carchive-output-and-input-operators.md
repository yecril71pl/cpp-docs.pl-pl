---
title: Korzystanie z CArchive &lt; &lt; i &gt; &gt; operatorów
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: 91ea565867cc0cb3b27ad9d5597037b637cb6544
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368961"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>Korzystanie z CArchive &lt; &lt; i &gt; &gt; operatorów

`CArchive`zapewnia operatorom \< <i >> do zapisywania i odczytywania prostych typów danych, a także `CObject`s do i z pliku.

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>Aby zapisać obiekt w pliku za pośrednictwem archiwum

1. W poniższym przykładzie pokazano, jak przechowywać obiekt w pliku za pośrednictwem archiwum:

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>Aby załadować obiekt z wartości wcześniej przechowywanej w pliku

1. W poniższym przykładzie pokazano, jak załadować obiekt z wartości wcześniej przechowywanej w pliku:

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

Zazwyczaj dane są przechowywane i ładowane do i `Serialize` z `CObject`pliku za pośrednictwem archiwum w funkcjach klas pochodnych, które muszą być zadeklarowane za pomocą makra DECLARE_SERIALIZE. Odwołanie do `CArchive` obiektu jest przekazywane `Serialize` do funkcji. Wywołanie `IsLoading` funkcji obiektu, `CArchive` aby ustalić, `Serialize` czy funkcja została wywołana, aby załadować dane z pliku lub przechowywać dane do pliku.

Funkcja `Serialize` klasy pochodnej `CObject`serializable zazwyczaj ma następujący formularz:

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

Powyższy szablon kodu jest dokładnie taki sam, jak `Serialize` jeden AppWizard tworzy dla `CDocument`funkcji dokumentu (klasa pochodząca z ). Ten szablon kodu pomaga napisać kod, który jest łatwiejszy do przejrzenia, ponieważ kod przechowywania i kod ładowania powinny być zawsze równoległe, jak w poniższym przykładzie:

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

Biblioteka definiuje ** < ** **>>** i `CArchive` operatorów jako pierwszy operand i następujące typy danych i typów klas jako drugi operand:

||||
|-|-|-|
|`CObject*`|**ROZMIAR** i`CSize`|**float**|
|**Word**|`CString`|**PUNKT** i`CPoint`|
|`DWORD`|**Bajtów**|`RECT` i `CRect`|
|**Podwójne**|**Długi**|`CTime` i `CTimeSpan`|
|`Int`|**Colecurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
> Przechowywanie i `CObject`ładowanie s za pośrednictwem archiwum wymaga dodatkowego rozważenia. Aby uzyskać więcej informacji, zobacz [Przechowywanie i ładowanie CObjects za pośrednictwem archiwum](../mfc/storing-and-loading-cobjects-via-an-archive.md).

**CArchive <\< ** i **>>** operatory zawsze zwracają odwołanie `CArchive` do obiektu, który jest pierwszym operand. Umożliwia to łańcuch operatorów, jak pokazano poniżej:

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>Zobacz też

[Serializacja: serializacja obiektu](../mfc/serialization-serializing-an-object.md)
