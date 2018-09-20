---
title: Za pomocą CArchive &lt; &lt; i &gt; &gt; operatory | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CArchive
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], loading from previously stored values
- CArchive class [MFC], storing and loading objects
- CArchive class [MFC], operators
ms.assetid: 56aef326-02dc-4992-8282-f0a4b78a064e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 49ea94258c163c241243934f41d55d896d0d1fa2
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2018
ms.locfileid: "46372460"
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>Za pomocą CArchive &lt; &lt; i &gt; &gt; operatorów

`CArchive` udostępnia <\< i >> operatory do zapisywania i odczytywania proste typy danych oraz `CObject`s do i z pliku.

#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>Do przechowywania obiektów w pliku za pomocą archiwum

1. Poniższy przykład pokazuje, jak przechowywać obiekt w pliku za pomocą archiwum:

     [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]

#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>Próba załadowania obiektu, z wartością wcześniej zapisane w pliku

1. Poniższy przykład pokazuje, jak próba załadowania obiektu, z wartością wcześniej zapisane w pliku:

     [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]

Zwykle, przechowywanie i ładowanie danych do i z pliku za pomocą archiwum w `Serialize` funkcji `CObject`-pochodne klasy, które musi mieć zadeklarowany za pomocą makra DECLARE_SERIALIZE. Odwołanie do `CArchive` obiekt jest przekazywany do usługi `Serialize` funkcji. Należy wywołać `IsLoading` funkcji `CArchive` obiektu, aby określić, czy `Serialize` funkcja została wywołana do ładowania danych z pliku ani do przechowywania danych do pliku.

`Serialize` Funkcji serializacji `CObject`-klasy pochodnej, zwykle ma następującą postać:

[!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]

Powyższego kodu szablonu jest dokładnie taka sama, co tworzy przez kreatora AppWizard `Serialize` funkcja dokumentu (klasą pochodną `CDocument`). Ten szablon kodu ułatwia pisanie kodu, który jest łatwiejsze do przeglądania, ponieważ kod przechowywania i kod ładujący powinna zawsze być równolegle, jak w poniższym przykładzie:

[!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]

Definiuje bibliotekę **< \<** i **>>** operatory `CArchive` jako pierwszy argument operacji i następujących typów danych oraz typy klas jako drugiego operandu :

||||
|-|-|-|
|`CObject*`|**ROZMIAR** i `CSize`|**float**|
|**WORD**|`CString`|**PUNKT** i `CPoint`|
|`DWORD`|**BAJTÓW**|`RECT` i `CRect`|
|**Double**|**DŁUGI**|`CTime` i `CTimeSpan`|
|`Int`|**COleCurrency**|`COleVariant`|
|`COleDateTime`|`COleDateTimeSpan`||

> [!NOTE]
>  Przechowywanie i ładowanie `CObject`s za pomocą archiwum wymaga dodatkowego rozważenia. Aby uzyskać więcej informacji, zobacz [przechowywanie i ładowanie obiektów CObject za pomocą archiwum](../mfc/storing-and-loading-cobjects-via-an-archive.md).

**CArchive <\<**  i **>>** operatory zawsze zwraca odwołanie do `CArchive` obiektu, który jest pierwszy operand. Dzięki temu można połączyć w łańcuch operatorów, jak przedstawiono poniżej:

[!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]

## <a name="see-also"></a>Zobacz też

[Serializacja: serializacja obiektu](../mfc/serialization-serializing-an-object.md)

