---
title: 'Formanty MFC ActiveX: Serializacja | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: f9db6ff6c0cdda01875e4968e4d92ca087ad2b57
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930064"
---
# <a name="mfc-activex-controls-serializing"></a>Kontrolki ActiveX MFC: serializacja
W tym artykule omówiono sposób zserializować formantu ActiveX. Serializacja jest proces Odczyt lub zapis na nośniku magazynu trwałego, takich jak pliku na dysku. Biblioteka Microsoft Foundation Class (MFC) udostępnia wbudowaną obsługę serializacji w klasie `CObject`. `COleControl` Rozszerza ta obsługa do formantu ActiveX przy użyciu właściwości mechanizm wymiany.  
  
 Serializacji dla formantów ActiveX jest implementowany przez zastępowanie [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). Tej funkcji, wywoływana podczas ładowania i zapisywanie obiektu kontroli przechowuje wszystkie właściwości zaimplementowany przy użyciu zmiennej członkowskiej lub zmiennej członkowskiej z powiadomienia o zmianie.  
  
 W poniższych tematach znajdziesz głównego problemy związane z formantu ActiveX serializacji:  
  
-   Implementowanie `DoPropExchange` do serializacji obiektu kontroli — funkcja  
  
-   [Dostosowywanie procesu serializacji](#_core_customizing_the_default_behavior_of_dopropexchange)  
  
-   [Implementowanie obsługi wersji](#_core_implementing_version_support)  
  
##  <a name="_core_implementing_the_dopropexchange_function"></a> Implementowanie funkcji DoPropExchange  
 Podczas generowania projektu kontroli za pomocą Kreatora formantu ActiveX, niektóre funkcje programu obsługi domyślne są automatycznie dodawane do klasy formantu, w tym Domyślna implementacja [COleControl::DoPropExchange](../mfc/reference/colecontrol-class.md#dopropexchange). W poniższym przykładzie pokazano kod dodany do klasy utworzone za pomocą Kreatora formantów ActiveX:  
  
 [!code-cpp[NVC_MFC_AxUI#43](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_1.cpp)]  
  
 Jeśli chcesz trwale zapisać właściwość, należy zmodyfikować `DoPropExchange` przez dodanie wywołanie funkcji exchange właściwości. W poniższym przykładzie pokazano serializacji właściwości niestandardowej CircleShape logiczna, której właściwość CircleShape ma wartość domyślną równą **TRUE**:  
  
 [!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]  
[!code-cpp[NVC_MFC_AxSer#2](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_3.cpp)]  
  
 W poniższej tabeli wymieniono funkcje programu exchange możliwe właściwości, które można serializować właściwości formantu:  
  
|Funkcje wymiany właściwości|Cel|  
|---------------------------------|-------------|  
|**Px_blob —)**|Serializuje typu właściwości danych binarnych duży obiekt (obiektów BLOB).|  
|**Px_bool —)**|Serializuje typu właściwości typu Boolean.|  
|**Px_color —)**|Serializuje typu właściwości color.|  
|**Px_currency —)**|Serializuje typu **CY** właściwości (currency).|  
|**Px_double —)**|Serializuje typu **podwójne** właściwości.|  
|**Px_font —)**|Serializuje właściwość Typ czcionki.|  
|**Px_float —)**|Serializuje typu **float** właściwości.|  
|**Px_iunknown —)**|Serializuje właściwość typu `LPUNKNOWN`.|  
|**Px_long —)**|Serializuje typu **długi** właściwości.|  
|**Px_picture —)**|Serializuje typu właściwości obrazu.|  
|**Px_short —)**|Serializuje typu **krótki** właściwości.|  
|**(PXstring)**|Serializuje typu `CString` właściwości.|  
|**Px_ulong —)**|Serializuje typu **ULONG** właściwości.|  
|**Px_ushort —)**|Serializuje typu **USHORT** właściwości.|  
  
 Aby uzyskać więcej informacji na temat tych właściwości funkcji programu exchange, zobacz [trwałości z OLE formanty](../mfc/reference/persistence-of-ole-controls.md) w *odwołania MFC*.  
  
##  <a name="_core_customizing_the_default_behavior_of_dopropexchange"></a> Dostosowywanie domyślnego zachowania DoPropExchange  
 Domyślna implementacja `DoPropertyExchange` (zgodnie z informacjami podanymi w temacie poprzedniej) nawiązuje połączenie klasa podstawowa `COleControl`. Serializuje to zbiór właściwości automatycznie obsługiwane przez `COleControl`, który używa więcej miejsca niż serializacja właściwości niestandardowe kontrolki. Usunięcie tego wywołania umożliwia obiekt można szeregować tylko właściwości, które należy wziąć pod uwagę ważne. Wszystkie stany właściwości standardowych zaimplementowała formantu nie będą wykonywane szeregowo podczas zapisywania lub wczytywania obiekt formantu, chyba że dodasz **PX_** odwołuje się do nich.  
  
##  <a name="_core_implementing_version_support"></a> Implementowanie obsługi wersji  
 Obsługa wersji umożliwia poprawione formantu ActiveX dodać nowe właściwości trwałych i nadal mieć możliwość wykrywania i załadować trwały stan utworzony we wcześniejszej wersji formantu. Aby udostępnić wersję formantu w ramach jego trwałych danych, należy wywołać [COleControl::ExchangeVersion](../mfc/reference/colecontrol-class.md#exchangeversion) w formancie `DoPropExchange` funkcji. To wywołanie jest automatycznie wstawiony, jeśli formant ActiveX został utworzony przy użyciu Kreatora formantów ActiveX. Można usunąć, jeśli nie jest potrzebna obsługa wersji. Jednak koszt rozmiar formantu jest bardzo mały (4 bajty) dodany elastyczność, która udostępnia obsługę wersji.  
  
 Jeśli formant nie został utworzony przy użyciu Kreatora formantu ActiveX, dodaj wywołanie do `COleControl::ExchangeVersion` wstawiając następujący wiersz na początku Twojej `DoPropExchange` — funkcja (przed wywołaniem do `COleControl::DoPropExchange`):  
  
 [!code-cpp[NVC_MFC_AxSer#1](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_2.cpp)]  
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]  
  
 Można użyć dowolnego **DWORD** jako numer wersji. Użyj projektów generowane przez kreatora formantu ActiveX `_wVerMinor` i `_wVerMajor` jako domyślny. Są to stałe globalne zdefiniowane w pliku implementacji klasy formantu ActiveX projektu. W pozostałej części sieci `DoPropExchange` funkcji, należy wywołać [CPropExchange::GetVersion](../mfc/reference/cpropexchange-class.md#getversion) w dowolnym momencie można pobrać wersji podczas zapisywania lub pobierania.  
  
 W poniższym przykładzie wersja 1 tego formantu próbki ma właściwość "ReleaseDate". W wersji 2 dodaje właściwość typu "OriginalDate". Jeśli formant jest instrukcją załadować trwały stan starszej wersji, inicjuje zmiennej członkowskiej dla nowych właściwości do wartości domyślnej.  
  
 [!code-cpp[NVC_MFC_AxSer#4](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_5.cpp)]  
[!code-cpp[NVC_MFC_AxSer#3](../mfc/codesnippet/cpp/mfc-activex-controls-serializing_4.cpp)]  
  
 Domyślnie formantu "konwertuje" stare dane do najnowszego formatu. Na przykład jeśli w wersji 2 formantu ładuje dane, który został zapisany w wersji 1, go zapisze formacie w wersji 2 po zapisaniu go ponownie. Jeśli chcesz kontrolować dane zapisane w formacie ostatniego odczytu, Przekaż **FALSE** jako trzeci parametr podczas wywoływania metody `ExchangeVersion`. Ten trzeci parametr jest opcjonalny i jest **TRUE** domyślnie.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

