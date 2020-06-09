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
ms.openlocfilehash: c06299f2fc7409476e4f5e5744ea11c962e3b173
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621201"
---
# <a name="mfc-activex-controls-serializing"></a>Kontrolki ActiveX MFC: serializacja

W tym artykule omówiono sposób serializacji kontrolki ActiveX. Serializacja jest procesem odczytu lub zapisu do trwałego nośnika magazynu, takiego jak plik dysku. Biblioteka Microsoft Foundation Class (MFC) zawiera wbudowaną obsługę serializacji w klasie `CObject` . `COleControl`rozszerza tę obsługę na kontrolki ActiveX przy użyciu mechanizmu wymiany właściwości.

>[!IMPORTANT]
> Kontrolka ActiveX to Starsza technologia, która nie powinna być używana do nowych celów programistycznych. Aby uzyskać więcej informacji na temat nowoczesnych technologii, które zastępują ActiveX, zobacz [kontrolki ActiveX](activex-controls.md).

Serializacja dla formantów ActiveX jest implementowana przez zastąpienie [COleControl::D opropexchange](reference/colecontrol-class.md#dopropexchange). Ta funkcja wywoływana podczas ładowania i zapisywania obiektu sterującego przechowuje wszystkie właściwości zaimplementowane ze zmienną członkowską lub zmienną członkowską z powiadomieniem o zmianie.

W poniższych tematach omówiono główne problemy związane z serializowaniem kontrolki ActiveX:

- Implementowanie `DoPropExchange` funkcji do serializacji obiektu formantu

- [Dostosowywanie procesu serializacji](#_core_customizing_the_default_behavior_of_dopropexchange)

- [Implementowanie obsługi wersji](#_core_implementing_version_support)

## <a name="implementing-the-dopropexchange-function"></a><a name="_core_implementing_the_dopropexchange_function"></a>Implementowanie funkcji DoPropExchange

W przypadku wygenerowania projektu kontrolki za pomocą Kreatora kontrolek ActiveX kilka domyślnych funkcji programu obsługi jest automatycznie dodawanych do klasy kontrolki, łącznie z domyślną implementacją [COleControl::D opropexchange](reference/colecontrol-class.md#dopropexchange). Poniższy przykład pokazuje kod dodany do klas utworzonych za pomocą Kreatora kontrolek ActiveX:

[!code-cpp[NVC_MFC_AxUI#43](codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

Jeśli chcesz uczynić Właściwość trwałą, zmodyfikuj ją `DoPropExchange` przez dodanie wywołania funkcji wymiany właściwości. Poniższy przykład ilustruje serializację niestandardowej wartości właściwości CircleShape, gdzie Właściwość CircleShape ma wartość domyślną **true**:

[!code-cpp[NVC_MFC_AxSer#1](codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

Poniższa tabela zawiera listę możliwych funkcji wymiany właściwości, których można użyć do serializacji właściwości kontrolki:

|Funkcje wymiany właściwości|Przeznaczenie|
|---------------------------------|-------------|
|**PX_Blob ()**|Serializować Właściwość danych obiektu binarnego typu binary (BLOB).|
|**PX_Bool ()**|Serializować Właściwość Boolean typu.|
|**PX_Color ()**|Serializować Właściwość koloru typu.|
|**PX_Currency ()**|Serializować właściwość typu **cy** (Currency).|
|**PX_Double ()**|Serializować Właściwość **Double** typu.|
|**PX_Font ()**|Serializować właściwość typu czcionki.|
|**PX_Float ()**|Serializować właściwość typu **zmiennoprzecinkowego** .|
|**PX_IUnknown ()**|Serializować właściwość typu `LPUNKNOWN` .|
|**PX_Long ()**|Serializować Właściwość **Long** typu.|
|**PX_Picture ()**|Serializować Właściwość obrazu typu.|
|**PX_Short ()**|Serializować **krótką** właściwość typu.|
|**PXstring( )**|Serializować `CString` Właściwość typu.|
|**PX_ULong ()**|Serializować właściwość typu **ULONG** .|
|**PX_UShort ()**|Serializować właściwość typu **UShort** .|

Aby uzyskać więcej informacji na temat tych funkcji wymiany właściwości, zobacz [trwałość formantów OLE](reference/persistence-of-ole-controls.md) w *Kompendium MFC*.

## <a name="customizing-the-default-behavior-of-dopropexchange"></a><a name="_core_customizing_the_default_behavior_of_dopropexchange"></a>Dostosowywanie domyślnego zachowania DoPropExchange

Domyślna implementacja programu `DoPropertyExchange` (jak pokazano w poprzednim temacie) wywołuje klasę bazową `COleControl` . Powoduje to serializacji zestawu właściwości obsługiwanych automatycznie przez `COleControl` program, który używa większej ilości miejsca do magazynowania niż Serializacja tylko właściwości niestandardowych formantu. Usunięcie tego wywołania umożliwia obiektowi Serializowanie tylko tych właściwości, które są uważane za ważne. We wszystkich właściwościach stanu zaimplementowany formant nie zostanie Zserializowany podczas zapisywania lub ładowania obiektu sterowania, chyba że jawnie dodasz **PX_** wywołania.

## <a name="implementing-version-support"></a><a name="_core_implementing_version_support"></a>Implementowanie obsługi wersji

Obsługa wersji umożliwia skorygowanie kontrolki ActiveX do dodawania nowych trwałych właściwości i nadal umożliwia wykrywanie i ładowanie stanu trwałego utworzonego przez wcześniejszą wersję formantu. Aby udostępnić wersję kontrolki jako część danych trwałych, wywołaj [COleControl:: ExchangeVersion](reference/colecontrol-class.md#exchangeversion) w `DoPropExchange` funkcji formantu. To wywołanie jest automatycznie wstawiane, jeśli Kontrolka ActiveX została utworzona za pomocą Kreatora kontrolki ActiveX. Można je usunąć, jeśli obsługa wersji nie jest wymagana. Jednak koszt w ramach kontroli jest bardzo mały (4 bajty), aby zwiększyć elastyczność oferowaną przez obsługę wersji.

Jeśli formant nie został utworzony za pomocą Kreatora kontrolki ActiveX, Dodaj wywołanie do, `COleControl::ExchangeVersion` wstawiając Poniższy wiersz na początku `DoPropExchange` funkcji (przed wywołaniem do `COleControl::DoPropExchange` ):

[!code-cpp[NVC_MFC_AxSer#1](codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Możesz użyć dowolnego **typu DWORD** jako numeru wersji. Projekty wygenerowane przez Kreatora formantów ActiveX są używane `_wVerMinor` i `_wVerMajor` domyślnie. Są to globalne stałe zdefiniowane w pliku implementacji klasy kontrolki ActiveX projektu. W pozostałej części `DoPropExchange` funkcji możesz w dowolnym momencie wywołać metodę [CPropExchange:: GetVersion](reference/cpropexchange-class.md#getversion) , aby pobrać zapisywany lub pobieraną wersję.

W poniższym przykładzie wersja 1 tej kontrolki przykładowej ma tylko właściwość "ReleaseDate". Wersja 2 dodaje właściwość "OriginalDate". Jeśli formant jest polecany do załadowania stanu trwałego ze starej wersji, inicjuje zmienną członkowską dla nowej właściwości do wartości domyślnej.

[!code-cpp[NVC_MFC_AxSer#4](codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Domyślnie kontrolka "konwertuje" stare dane do najnowszego formatu. Na przykład jeśli wersja 2 kontrolki wczytuje dane zapisane w wersji 1, program zapisze format wersji 2 po ponownym zapisaniu. Jeśli chcesz, aby formant zapisywał dane w formacie ostatnim odczytu, Przekaż **false** jako trzeci parametr podczas wywoływania `ExchangeVersion` . Ten trzeci parametr jest opcjonalny i domyślnie ma **wartość true** .

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](mfc-activex-controls.md)
