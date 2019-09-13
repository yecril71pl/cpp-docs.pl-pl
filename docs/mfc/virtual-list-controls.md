---
title: Wirtualne formanty listy
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: a6e76a812a6196c487f72516e2b88198a544fdc7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907344"
---
# <a name="virtual-list-controls"></a>Wirtualne formanty listy

Formant listy wirtualnej to kontrolka widoku listy, która ma styl LVS_OWNERDATA. Ten styl umożliwia formantowi obsługę liczby elementów do wartości **DWORD** (domyślna liczba elementów rozciąga się tylko na **int**). Jednak największą zaletą zapewnianą przez ten styl jest możliwość tylko jednego podzbioru elementów danych w pamięci. Dzięki temu kontrolka widok listy wirtualnej może być używana z dużymi bazami danych informacji, w których określone metody uzyskiwania dostępu do danych są już na miejscu.

> [!NOTE]
>  Oprócz udostępniania funkcji listy wirtualnej w programie `CListCtrl`MFC zapewnia również te same funkcje w klasie [CListView](../mfc/reference/clistview-class.md) .

Istnieją pewne problemy ze zgodnością, które należy wziąć pod uwagę podczas tworzenia formantów listy wirtualnej. Aby uzyskać więcej informacji, zobacz sekcję problemy ze zgodnością w temacie kontrolki widoku listy w Windows SDK.

## <a name="handling-the-lvn_getdispinfo-notification"></a>Obsługa powiadomienia LVN_GETDISPINFO

Kontrolki listy wirtualnej utrzymują bardzo małe informacje o elemencie. Oprócz wyboru elementów i informacji o koncentracji wszystkie informacje o elemencie są zarządzane przez właściciela kontrolki. Dane są żądane przez platformę za pośrednictwem LVN_GETDISPINFO komunikatu z powiadomieniem. Aby zapewnić żądane informacje, właściciel kontrolki listy wirtualnej (lub sam formant) musi obsłużyć to powiadomienie. Można to łatwo zrobić przy użyciu [kreatora klas](reference/mfc-class-wizard.md) (zobacz [Mapowanie komunikatów do funkcji](../mfc/reference/mapping-messages-to-functions.md)). Wynikowy kod powinien wyglądać podobnie do poniższego przykładu (gdzie `CMyDialog` jest właścicielem obiektu kontrolki listy wirtualnej, a okno dialogowe obsługuje powiadomienie):

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

W programie obsługi komunikatu powiadomienia LVN_GETDISPINFO należy sprawdzić, jakiego typu informacje są żądane. Możliwe wartości to:

- `LVIF_TEXT`Składowa *pszText* musi być wypełniona.

- `LVIF_IMAGE`Składowa *IImage* musi być wypełniona.

- `LVIF_INDENT`Składowa *iIndent* musi być wypełniona.

- `LVIF_PARAM`Składowa *lParam* musi być wypełniona. (Nieobecne dla elementów podrzędnych).

- `LVIF_STATE`Należy podać element członkowski *stanu* .

Następnie należy podać, jakie informacje są wymagane z powrotem do struktury.

Poniższy przykład (pobrany z treści procedury obsługi powiadomień dla obiektu formant listy) pokazuje jedną z możliwych metod, dostarczając informacje dla buforów tekstu i obrazu elementu:

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>Buforowanie i kontrolki listy wirtualnej

Ponieważ ten typ kontrolki listy jest przeznaczony dla dużych zestawów danych, zaleca się buforowanie żądanych danych elementów w celu zwiększenia wydajności pobierania. Struktura zapewnia mechanizm podręczny, który ułatwia optymalizację pamięci podręcznej przez wysłanie komunikatu powiadomienia LVN_ODCACHEHINT.

Poniższy przykład aktualizuje pamięć podręczną z zakresem przesłanym do funkcji obsługi.

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

Aby uzyskać więcej informacji na temat przygotowywania i konserwowania pamięci podręcznej, zobacz sekcję Zarządzanie pamięcią podręczną w temacie kontrolki widoku listy w Windows SDK.

## <a name="finding-specific-items"></a>Znajdowanie określonych elementów

Komunikat powiadomienia LVN_ODFINDITEM jest wysyłany przez kontrolkę listy wirtualnej, gdy należy znaleźć określony element formantu listy. Komunikat powiadomienia jest wysyłany, gdy kontrolka widok listy odbierze szybki dostęp do klucza lub gdy odbierze komunikat LVM_FINDITEM. Informacje o wyszukiwaniu są wysyłane w formie struktury **LVFINDINFO** , która jest elementem członkowskim struktury **NMLVFINDITEM** . Obsłuż ten komunikat, zastępując `OnChildNotify` funkcję obiektu formantu listy i wewnątrz treści programu obsługi, sprawdź, czy jest wyświetlany komunikat LVN_ODFINDITEM. W przypadku znalezienia należy wykonać odpowiednią akcję.

Należy przygotować się do wyszukania elementu, który odpowiada informacjom podanym przez formant widoku listy. Należy zwrócić indeks elementu, jeśli to się powiedzie, lub-1, jeśli nie zostanie znaleziony pasujący element.

## <a name="see-also"></a>Zobacz także

[Korzystanie z CListCtrl](../mfc/using-clistctrl.md)<br/>
[Kontrolki](../mfc/controls-mfc.md)
