---
title: 'Kontrolki ActiveX MFC: Serializacja | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- _wVerMinor
- DoPropExchange
- _wVerMajor
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cf2568561e3e79eaf7c2f56b0b571f5c9e74f268
ms.sourcegitcommit: a3c9e7888b8f437a170327c4c175733ad9eb0454
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2018
ms.locfileid: "50204525"
---
# <a name="mfc-activex-controls-serializing"></a>Kontrolki ActiveX MFC: serializacja

W tym artykule omówiono sposób serializacji formantu ActiveX. Serializacja jest proces odczytu / zapisu na nośnik z magazynu trwałego, na przykład plik dysku. Biblioteka Microsoft Foundation Class (MFC) udostępnia wbudowaną obsługę serializacji w klasie `CObject`. `COleControl` Rozszerza tę obsługę do formantów ActiveX przy użyciu właściwości mechanizm wymiany.

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które zastępują ActiveX zobacz [formantów ActiveX](activex-controls.md).

Serializacji dla formantów ActiveX jest implementowany przez zastąpienie [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). Ta funkcja wywoływana podczas ładowania i zapisywania obiektu kontroli przechowuje wszystkie właściwości implementowane za pomocą zmiennej członkowskiej lub zmienną składową za pomocą powiadomienia o zmianie.

W poniższych tematach znajdziesz główne kwestie związane z formantu ActiveX serializacji:

- Implementowanie `DoPropExchange` funkcji do serializacji obiektu formantu

- [Dostosowywanie procesu serializacji](#_core_customizing_the_default_behavior_of_dopropexchange)

- [Implementowanie obsługi wersji](#_core_implementing_version_support)

##  <a name="_core_implementing_the_dopropexchange_function"></a> Implementacja funkcji DoPropExchange

Gdy używasz kreatora kontrolek ActiveX do generowania projektu kontroli kilka funkcji obsługi domyślne są automatycznie dodawane do klasy kontrolki, w tym domyślna Implementacja klasy [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). Poniższy przykład przedstawia kod dodany do klasy utworzone za pomocą Kreatora kontrolek ActiveX:

[!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]

Jeśli chcesz trwale zapisać właściwości, należy zmodyfikować `DoPropExchange` , dodając wywołania funkcji exchange właściwości. W poniższym przykładzie pokazano serializacji właściwość niestandardową CircleShape logiczna, której właściwość CircleShape ma wartość domyślną **TRUE**:

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]

W poniższej tabeli wymieniono funkcje programu exchange możliwymi właściwościami, służących do wykonywania serializacji właściwości formantu:

|Funkcje wymiany właściwości|Cel|
|---------------------------------|-------------|
|**Px_blob —)**|Serializuje typ właściwości danych binarnych dużych obiektów (BLOB).|
|**Px_bool —)**|Serializuje typ właściwości typu Boolean.|
|**Px_color —)**|Serializuje typ właściwości color.|
|**Px_currency —)**|Serializuje typu **CY** właściwości (currency).|
|**Px_double —)**|Serializuje typu **double** właściwości.|
|**Px_font —)**|Serializuje właściwość Typ czcionki.|
|**Px_float —)**|Serializuje typu **float** właściwości.|
|**Px_iunknown —)**|Serializuje właściwość typu `LPUNKNOWN`.|
|**Px_long —)**|Serializuje typu **długie** właściwości.|
|**Px_picture —)**|Serializuje typ właściwości obrazu.|
|**Px_short —)**|Serializuje typu **krótki** właściwości.|
|**(PXstring)**|Serializuje typu `CString` właściwości.|
|**Px_ulong —)**|Serializuje typu **ULONG** właściwości.|
|**Px_ushort —)**|Serializuje typu **USHORT** właściwości.|

Aby uzyskać więcej informacji na temat tych funkcji exchange właściwości, zobacz [stanu trwałego elementu OLE kontrolki](../mfc/reference/persistence-of-ole-controls.md) w *odwołanie MFC*.

##  <a name="_core_customizing_the_default_behavior_of_dopropexchange"></a> Dostosowywanie domyślnego zachowania DoPropExchange

Domyślna implementacja klasy `DoPropertyExchange` (jak pokazano w poprzednim temacie) wykonuje wywołania do klasy bazowej `COleControl`. Serializuje to zbiór właściwości automatycznie obsługiwane przez `COleControl`, który używa więcej miejsca niż serializowania właściwości niestandardowe kontrolki. Usunięcie tego wywołania umożliwia obiektu do zserializowania tylko te właściwości, które uznasz za istotne. Wszystkie stany właściwości podstawowych kontrolki została zaimplementowana. nie można serializować podczas zapisywania lub wczytywania obiekt formantu, chyba że dodasz **PX_** wywołuje dla nich.

##  <a name="_core_implementing_version_support"></a> Implementowanie obsługi wersji

Obsługa wersji umożliwia poprawione formantu ActiveX, dodawać nowe właściwości trwałe i nadal mieć możliwość wykrywania i załadować trwały stan utworzone przez starszą wersję kontrolki. Aby udostępnić kontroli wersji w ramach jego trwałych danych, należy wywołać [COleControl::ExchangeVersion](../mfc/reference/colecontrol-class.md#exchangeversion) w formancie `DoPropExchange` funkcji. To wywołanie jest wstawiany automatycznie, jeśli formant ActiveX został utworzony przy użyciu Kreatora kontrolek ActiveX. Można je usunąć, jeśli nie jest wymagana obsługa wersji. Jednak koszt rozmiaru kontrolki jest bardzo mały (4 bajtów) dla dodatkową elastyczność, która zapewnia obsługę wersji.

Jeśli formant nie został utworzony za pomocą Kreatora kontrolek ActiveX, należy dodać wywołanie `COleControl::ExchangeVersion` , wstawiając następujący wiersz na początku swoje `DoPropExchange` — funkcja (przed wywołaniem do `COleControl::DoPropExchange`):

[!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Możesz użyć dowolnej **DWORD** jako numer wersji. Projekty generowane przez kreatora kontrolek ActiveX korzystają `_wVerMinor` i `_wVerMajor` jako domyślny. Są to stałe globalne zdefiniowane w pliku implementacji klasy kontrolki ActiveX projektu. W pozostałej części Twojej `DoPropExchange` funkcji, można wywołać [CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion) w dowolnym momencie można pobrać wersji podczas zapisywania lub pobierania.

W poniższym przykładzie wersja 1 tej kontrolki przykładowe ma właściwość "ReleaseDate". W wersji 2 dodaje właściwość "OriginalDate". Jeśli formant jest zobowiązany do załadowania trwały stan ze starej wersji, inicjuje zmienną elementu członkowskiego dla nowej właściwości na wartość domyślną.

[!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]

Domyślnie formant "konwertuje" stare dane do najnowszego formatu. Na przykład jeśli formant w wersji 2 ładuje dane, który został zapisany w wersji 1, jego zapisze format wersji 2 po zapisaniu go ponownie. Jeśli chcesz kontrolować dane zapisane w formacie ostatniego przeczytanego, przekazać **FALSE** jako trzeci parametr podczas wywoływania `ExchangeVersion`. To trzeci parametr jest opcjonalny, a także jest **TRUE** domyślnie.

## <a name="see-also"></a>Zobacz też

[Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

