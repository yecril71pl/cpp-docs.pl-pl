---
title: Przy użyciu CArchive &lt; &lt; i &gt; &gt; operatory | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 82b729caaa650fde72741497d3f4ab3c131f46ab
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-the-carchive-ltlt-and-gtgt-operators"></a>Przy użyciu CArchive &lt; &lt; i &gt; &gt; operatory
`CArchive` udostępnia <\< i >> operatory do zapisywania i odczytywania proste typy danych jak również `CObject`s do i z pliku.  
  
#### <a name="to-store-an-object-in-a-file-via-an-archive"></a>Próba zapisania obiektu w pliku za pomocą archiwum  
  
1.  Poniższy przykład przedstawia sposób zapisania obiektu w pliku za pomocą archiwum:  
  
     [!code-cpp[NVC_MFCSerialization#7](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_1.cpp)]  
  
#### <a name="to-load-an-object-from-a-value-previously-stored-in-a-file"></a>Próba załadowania obiektu, z wartością wcześniej są przechowywane w pliku  
  
1.  Poniższy przykład przedstawia sposób załadować obiekt z wartością wcześniej są przechowywane w pliku:  
  
     [!code-cpp[NVC_MFCSerialization#8](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_2.cpp)]  
  
 Zwykle, przechowywanie i ładowanie danych do i z pliku za pomocą archiwum w `Serialize` funkcje `CObject`-pochodzi z klasy, które musi być zadeklarowany z **DECLARE_SERIALIZE** makra. Odwołanie do `CArchive` obiekt jest przekazywany do Twojej `Serialize` funkcji. Należy wywołać `IsLoading` funkcji `CArchive` obiektem, aby określić czy `Serialize` została wywołana funkcja ładowania danych z pliku lub przechowywać dane w pliku.  
  
 `Serialize` Funkcji serializacji `CObject`— Klasa pochodna zwykle ma następujący format:  
  
 [!code-cpp[NVC_MFCSerialization#9](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_3.cpp)]  
  
 Powyższego szablonu kodu jest dokładnie taka sama, jak kreatorami AppWizard tworzy dla `Serialize` funkcja dokumentu (klasą pochodną **CDocument)**. Ten szablon kodu ułatwia pisanie kodu, który jest łatwiejsze do przeglądania, ponieważ kod przechowywania i kod ładujący zawsze powinny być równoległe, jak w poniższym przykładzie:  
  
 [!code-cpp[NVC_MFCSerialization#10](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_4.cpp)]  
  
 Definiuje biblioteki **< \<** i **>>** operatory `CArchive` jako pierwszy argument operacji i następujących typów danych oraz typy klas jako drugi argument operacji :  
  
||||  
|-|-|-|  
|`CObject*`|**ROZMIAR i CSize**|**float**|  
|**WORD**|`CString`|**PUNKT** i `CPoint`|  
|`DWORD`|**BAJTÓW**|`RECT` I `CRect`|  
|**Double**|**DŁUGA**|`CTime` I `CTimeSpan`|  
|`Int`|**COleCurrency**|`COleVariant`|  
|`COleDateTime`|`COleDateTimeSpan`||  
  
> [!NOTE]
>  Przechowywanie i ładowanie `CObject`s za pomocą archiwum wymaga dodatkowego rozważenia. Aby uzyskać więcej informacji, zobacz [przechowywanie i ładowanie obiektów CObjects za pomocą archiwum](../mfc/storing-and-loading-cobjects-via-an-archive.md).  
  
 **CArchive <\<**  i **>>** operatory zawsze zwraca odwołanie do `CArchive` obiektu, który jest pierwszym argumentem. Umożliwia to łańcucha operatorów, jak przedstawiono poniżej:  
  
 [!code-cpp[NVC_MFCSerialization#11](../mfc/codesnippet/cpp/using-the-carchive-output-and-input-operators_5.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja: serializacja obiektu](../mfc/serialization-serializing-an-object.md)

