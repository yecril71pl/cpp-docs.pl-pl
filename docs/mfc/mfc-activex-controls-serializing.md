---
title: 'Kontrolki ActiveX MFC: serializacja'
ms.date: 09/12/2018
f1_keywords:
- _wVerMinor
- DoPropExchange
- _wVerMajor
helpviewer_keywords:
- MFC ActiveX controls [MFC], version support
- wVerMinor global constant [MFC]
- GetVersion method [MFC]
- ExchangeVersion method [MFC]
- MFC ActiveX controls [MFC], serializing
- DoPropExchange method [MFC]
- versioning ActiveX controls
- wVerMajor global constant
ms.assetid: 9d57c290-dd8c-4853-b552-6f17f15ebedd
ms.openlocfilehash: d804486b612906f537b6ed1665dfc0cec5149826
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364556"
---
# <a name="mfc-activex-controls-serializing"></a>Kontrolki ActiveX MFC: serializacja

W tym artykule omówiono sposób serializacji formantu ActiveX. Serializacja to proces odczytu lub zapisu na trwałym nośniku pamięci, takim jak plik dysku. Biblioteka Microsoft Foundation Class (MFC) zapewnia wbudowaną `CObject`obsługę serializacji w klasie. `COleControl`rozszerza tę obsługę do formantów ActiveX za pomocą mechanizmu wymiany właściwości.

>[!IMPORTANT]
> ActiveX to starsza technologia, która nie powinna być używana do nowego rozwoju. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [ActiveX Controls](activex-controls.md).

Serializacja dla formantów ActiveX jest implementowana przez zastąpienie [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). Ta funkcja, wywoływana podczas ładowania i zapisywania obiektu sterującego, przechowuje wszystkie właściwości zaimplementowane ze zmienną elementu członkowskiego lub zmienną elementu członkowskiego z powiadomieniem o zmianie.

Następujące tematy obejmują główne problemy związane z serializowaniem formantu ActiveX:

- Implementowanie `DoPropExchange` funkcji do serializacji obiektu sterującego

- [Dostosowywanie procesu serializacji](#_core_customizing_the_default_behavior_of_dopropexchange)

- [Obsługa wersji implementująca](#_core_implementing_version_support)

## <a name="implementing-the-dopropexchange-function"></a><a name="_core_implementing_the_dopropexchange_function"></a>Implementowanie funkcji DoPropExchange

Podczas generowania projektu sterującego za pomocą Kreatora sterowania ActiveX do generowania, kilka domyślnych funkcji obsługi jest automatycznie dodawanych do klasy sterowania, w tym domyślna implementacja [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). W poniższym przykładzie pokazano kod dodany do klas utworzonych za pomocą Kreatora sterowania ActiveX:

[!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

Jeśli chcesz, aby właściwość `DoPropExchange` trwała, zmodyfikuj, dodając wywołanie funkcji wymiany właściwości. W poniższym przykładzie pokazano serializacji niestandardowej właściwości Boolean CircleShape, gdzie właściwość CircleShape ma domyślną wartość **TRUE:**

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

W poniższej tabeli wymieniono możliwe funkcje wymiany właściwości, których można użyć do serializacji właściwości formantu:

|Funkcje wymiany nieruchomości|Przeznaczenie|
|---------------------------------|-------------|
|**PX_Blob( )**|Serializuje właściwość danych typu Binary Large Object (BLOB).|
|**PX_Bool( )**|Serializuje właściwość typu Boolean.|
|**PX_Color( )**|Serializuje właściwość koloru typu.|
|**PX_Currency( )**|Serializuje właściwość typu **CY** (waluta).|
|**PX_Double( )**|Serializuje właściwość typu **double.**|
|**PX_Font( )**|Serializuje właściwość typu Czcionka.|
|**PX_Float( )**|Serializuje właściwość **typu float.**|
|**PX_IUnknown( )**|Serializuje właściwość typu `LPUNKNOWN`.|
|**PX_Long( )**|Serializuje właściwość **typu long.**|
|**PX_Picture( )**|Serializuje typ Picture właściwości.|
|**PX_Short( )**|Serializuje właściwość **typu short.**|
|**PXstring( )**|Serializuje właściwość `CString` typu.|
|**PX_ULong( )**|Serializuje typ **ULONG** właściwości.|
|**PX_UShort( )**|Serializuje typ **USHORT** właściwości.|

Aby uzyskać więcej informacji na temat tych funkcji wymiany właściwości, zobacz [trwałość formantów OLE](../mfc/reference/persistence-of-ole-controls.md) w *odwołaniu MFC*.

## <a name="customizing-the-default-behavior-of-dopropexchange"></a><a name="_core_customizing_the_default_behavior_of_dopropexchange"></a>Dostosowywanie domyślnego zachowania DoPropExchange

Domyślna implementacja `DoPropertyExchange` (jak pokazano w poprzednim temacie) `COleControl`wywołuje klasę podstawową . To serializuje zestaw właściwości automatycznie obsługiwane przez `COleControl`program , który zużywa więcej miejsca do magazynowania niż serializacji tylko właściwości niestandardowe formantu. Usunięcie tego wywołania umożliwia obiektowi serializowanie tylko tych właściwości, które uważasz za ważne. Wszystkie stany właściwości magazynu formantu nie zostaną seriaryzowane podczas zapisywania lub ładowania obiektu kontrolnego, chyba że jawnie dodać **PX_** wywołania dla nich.

## <a name="implementing-version-support"></a><a name="_core_implementing_version_support"></a>Obsługa wersji implementująca

Obsługa wersji umożliwia poprawione ActiveX formantu, aby dodać nowe trwałe właściwości i nadal być w stanie wykryć i załadować stan trwały utworzony przez wcześniejszą wersję formantu. Aby udostępnić wersję formantu jako część jego danych trwałych, wywołaj [COleControl::ExchangeVersion](../mfc/reference/colecontrol-class.md#exchangeversion) w `DoPropExchange` funkcji formantu. To wywołanie jest automatycznie wstawiane, jeśli formant ActiveX został utworzony za pomocą Kreatora sterowania ActiveX. Można go usunąć, jeśli obsługa wersji nie jest potrzebna. Jednak koszt w rozmiarze formantu jest bardzo mały (4 bajty) dla dodatkowej elastyczności, że zapewnia obsługę wersji.

Jeśli formant nie został utworzony za pomocą Kreatora `COleControl::ExchangeVersion` sterowania ActiveX, dodaj wywołanie, wstawiając następujący wiersz na początku `DoPropExchange` funkcji (przed `COleControl::DoPropExchange`wywołaniem):

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Jako numer wersji można użyć dowolnego **dwordu.** Projekty generowane przez Kreatora `_wVerMinor` sterowania `_wVerMajor` ActiveX używają i są domyślne. Są to stałe globalne zdefiniowane w pliku implementacji klasy kontroli ActiveX projektu. W pozostałej `DoPropExchange` części funkcji można wywołać [CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion) w dowolnym momencie, aby pobrać wersję, którą zapisujesz lub pobierasz.

W poniższym przykładzie wersja 1 tego przykładowego formantu ma tylko właściwość "ReleaseDate". Wersja 2 dodaje właściwość "OriginalDate". Jeśli formant jest poinstruowany, aby załadować stan trwały ze starej wersji, inicjuje zmienną elementu członkowskiego dla nowej właściwości do wartości domyślnej.

[!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Domyślnie formant "konwertuje" stare dane na najnowszy format. Na przykład jeśli wersja 2 formantu ładuje dane, które zostały zapisane przez wersję 1, będzie pisać format w wersji 2, gdy jest zapisywany ponownie. Jeśli chcesz, aby formant zapisywał dane **FALSE** w formacie ostatniego `ExchangeVersion`odczytu, przekaż FALSE jako trzeci parametr podczas wywoływania . Ten trzeci parametr jest opcjonalny i domyślnie **ma wartość TRUE.**

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)
