---
title: Korzystanie z CArchive &lt;&lt; i &gt;operatory &gt;
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
ms.openlocfilehash: 8e175f35f2218341c69571c818711596180df4a6
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442177"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>Korzystanie z CArchive &lt;&lt; i &gt;operatory &gt;

`CArchive` zapewnia <\< i > operatory > do zapisywania i odczytywania prostych typów danych, a także `CObject`s do i z pliku.

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>Aby zapisać obiekt w pliku za pośrednictwem archiwum

1. Poniższy przykład pokazuje, jak przechowywać obiekt w pliku za pośrednictwem archiwum:

   [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>Aby załadować obiekt z wartości wcześniej przechowywanej w pliku

1. Poniższy przykład pokazuje, jak załadować obiekt z wartości poprzednio przechowywanej w pliku:

   [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

Zwykle przechowujesz i ładujesz dane do i z pliku za pośrednictwem archiwum w `Serialize` funkcje klas pochodnych `CObject`, które należy zadeklarować za pomocą makra DECLARE_SERIALIZE. Odwołanie do obiektu `CArchive` jest przesyłane do funkcji `Serialize`. Należy wywołać funkcję `IsLoading` obiektu `CArchive`, aby określić, czy funkcja `Serialize` została wywołana w celu załadowania danych z pliku lub zapisania danych do pliku.

Funkcja `Serialize` serializowanej `CObject`klasy pochodnej zazwyczaj ma następującą postać:

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

Powyższy szablon kodu jest dokładnie taki sam jak jeden AppWizard tworzony dla funkcji `Serialize` dokumentu (Klasa pochodna `CDocument`). Ten szablon kodu ułatwia pisanie kodu, który jest łatwiejszy do przejrzenia, ponieważ kod przechowywania i kod ładowania powinny zawsze być równoległe, tak jak w poniższym przykładzie:

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

Biblioteka definiuje **<\<** i operatory **>>** dla `CArchive` jako pierwszy operand i następujące typy danych i typy klas jako drugi operand:

||||
|-|-|-|
|`CObject*`|**Rozmiar** i `CSize`|**float**|
|**WORD**|`CString`|**Wskaż** i `CPoint`|
|`DWORD`|**BAJC**|`RECT` i `CRect`|
|**Double**|**DŁUGO**|`CTime` i `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
>  Przechowywanie i ładowanie `CObject`s za pośrednictwem archiwum wymaga dodatkowej uwagi. Aby uzyskać więcej informacji, zobacz artykuł [przechowywanie i ładowanie obiektów CObject za pomocą archiwum](../mfc/storing-and-loading-cobjects-via-an-archive.md).

Operatory **CArchive <\<** i **>>** zawsze zwracają odwołanie do obiektu `CArchive`, który jest pierwszym operandem. Pozwala to na łańcuch operatorów, jak pokazano poniżej:

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>Zobacz też

[Serializacja: serializacja obiektu](../mfc/serialization-serializing-an-object.md)
