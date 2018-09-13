---
title: 'Kontrolki ActiveX MFC: Lokalizowanie kontrolki ActiveX | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- LocaleID
- AfxOleRegisterTypeLib
dev_langs:
- C++
helpviewer_keywords:
- localization, ActiveX controls
- MFC ActiveX controls [MFC], localizing
- LocaleID ambient property [MFC]
- LOCALIZE sample [MFC]
ms.assetid: a44b839a-c652-4ec5-b824-04392708a5f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f8eb474a0d527ca6673d6c50602e0914f10bbf76
ms.sourcegitcommit: b4432d30f255f0cb58dce69cbc8cbcb9d44bc68b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45535031"
---
# <a name="mfc-activex-controls-localizing-an-activex-control"></a>Kontrolki ActiveX MFC: lokalizowanie kontrolki ActiveX
W tym artykule omówiono procedury lokalizowanie interfejsów kontrolki ActiveX.  

>[!IMPORTANT]
> ActiveX jest technologią starszą, która nie powinny być używane w przypadku nowych wdrożeń. Aby uzyskać więcej informacji na temat nowych technologii, które wypierają ActiveX zobacz [formantów ActiveX](activex-controls.md).
  
 Jeśli chcesz dostosować kontrolki ActiveX na rynku międzynarodowym można zlokalizować formantu. Windows obsługuje wiele języków, oprócz domyślnych angielski, niemiecki, francuski i szwedzki. Może powodować problemy dla formantu, jeśli jego interfejs jest tylko w języku angielskim.  
  
 Ogólnie rzecz biorąc kontrolek ActiveX zawsze należy oprzeć ich ustawienia regionalne na zmieniono właściwość identyfikator ustawień regionalnych. Istnieją trzy sposoby, w tym celu:  
  
-   Ładowanie zasobów, zawsze na żądanie, w oparciu o bieżącą wartość właściwości otoczenia identyfikator ustawień regionalnych. Przykładowe kontrolki MFC ActiveX [LOKALIZUJ](../visual-cpp-samples.md) korzysta z tej strategii.  
  
-   Ładowanie zasobów, gdy pierwszy formant jest wystąpienia, na podstawie właściwości otoczenia identyfikator ustawień regionalnych, a dzięki tym zasobom dla wszystkich innych wystąpień. W tym artykule przedstawiono tej strategii.  
  
    > [!NOTE]
    >  To nie będzie działać prawidłowo w niektórych przypadkach, jeśli w przyszłości wystąpień różnych ustawień regionalnych.  
  
-   Użyj `OnAmbientChanged` funkcję powiadomień, aby załadować dynamicznie do odpowiednich zasobów dla ustawień regionalnych kontenera.  
  
    > [!NOTE]
    >  Będzie to działać dla formantu, ale biblioteki wykonawczej DLL nie dynamicznie zaktualizuje własnych zasobów po zmianie właściwości otoczenia identyfikator ustawień regionalnych. Ponadto wykonawczej DLL dla formantów ActiveX użyj ustawienia regionalne wątku, aby określić ustawienia regionalne dla jego zasobów.  
  
 W pozostałej części tego artykułu opisano dwa lokalizowanie strategie. Pierwsza strategia [lokalizuje interfejs programowania formantu](#_core_localizing_your_control.92.s_programmability_interface) (nazwy właściwości, metody i zdarzenia). Druga strategia [lokalizuje interfejsu użytkownika formantu](#_core_localizing_the_control.92.s_user_interface), za pomocą kontenera właściwości identyfikator ustawień regionalnych. Demonstracyjne lokalizacji formantu, zobacz przykład kontrolki MFC ActiveX [LOKALIZUJ](../visual-cpp-samples.md).  
  
##  <a name="_core_localizing_your_control.92.s_programmability_interface"></a> Lokalizowanie formantu programowania interfejsu  
 Lokalizowanie formantu programowania interfejsu (interfejs używany przez programistów pisania aplikacji, które używają formantu), należy utworzyć zmodyfikowaną wersję kontrolki. IDL pliku (skrypt do tworzenia biblioteki typu formantu) dla każdego z języków, które zamierzasz obsługiwać. To jest jedynym miejscem, musisz zlokalizować nazwami właściwości kontrolek.  
  
 Podczas opracowywania formant zlokalizowany obejmują identyfikator ustawień regionalnych jako atrybut na poziomie biblioteki typów. Na przykład jeśli chcesz udostępnić bibliotekę typów o nazwach francuska zlokalizowanej właściwości, należy utworzyć kopię Twojego PRZYKŁADU. IDL pliku, a następnie wywołaj ją SAMPLEFR. IDL. Dodaj atrybut Identyfikatora ustawień regionalnych do pliku (identyfikator ustawień regionalnych, francuski jest 0x040c), podobny do następującego:  
  
 [!code-cpp[NVC_MFC_AxLoc#1](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_1.idl)]  
  
 Zmień nazwy właściwości w SAMPLEFR. IDL do ich odpowiedników francuska, a następnie użyj z MKTYPLIB. Plik EXE, aby tworzyć francuskich wpisz biblioteki SAMPLEFR. TLB.  
  
 Aby utworzyć wiele bibliotek typów zlokalizowane można dodać zlokalizowane. IDL, pliki do projektu i będzie on kompilowany automatycznie.  
  
#### <a name="to-add-an-idl-file-to-your-activex-control-project"></a>Aby dodać. Plik IDL projektu kontrolki ActiveX  
  
1.  Za pomocą projektu kontroli otwarty na **projektu** menu, kliknij przycisk **Dodaj istniejący element**.  
  
     **Dodaj istniejący element** pojawi się okno dialogowe.  
  
2.  Jeśli to konieczne, należy wybrać dysk i katalog, aby wyświetlić.  
  
3.  W **pliki typu** wybierz opcję **wszystkie pliki (\*.\*)** .  
  
4.  W polu listy plików, kliknij dwukrotnie. Plik IDL, który ma zostać wstawiony do projektu.  
  
5.  Kliknij przycisk **Otwórz** po dodaniu wszystkich niezbędnych. IDL, pliki.  
  
 Pliki zostały dodane do projektu, zostaną one skompilowane podczas kompilowania pozostałej części projektu. Biblioteki typów zlokalizowane znajdują się w bieżącym katalogu projektu kontrolki ActiveX.  
  
 W kodzie nazwy właściwości wewnętrznej (zwykle w języku angielskim) są zawsze używane i nigdy nie są zlokalizowane. W tym mapy wysyłania formantów, funkcje programu exchange właściwości i kodzie wymiany danych strony właściwości.  
  
 Tylko jeden typ biblioteki (. Plik TLB) może być powiązany z zasobów w implementacji kontroli (. Plik OCX). Zazwyczaj jest to wersja, która znormalizowanych (zwykle w języku angielskim) nazwy. Dostarczanie zlokalizowaną wersję Twoją kontrolą, musisz wysłać. OCX (która już została powiązana z domyślna. Wersja TLB) i. TLB dla odpowiednich ustawień regionalnych. Oznacza to, że tylko. OCX jest potrzebna dla angielskiej wersji od poprawny. TLB jest już powiązane do niego. Dla innych ustawień regionalnych, biblioteka typów zlokalizowane również musi być dostarczane z. OCX.  
  
 Aby upewnić się, że klienci kontrolki można znaleźć biblioteki typów zlokalizowane, zarejestrować Twoje specyficzne dla ustawień regionalnych. TLB plików, przejdź do sekcji biblioteki typów w rejestrze systemu Windows. Trzeci parametr (zwykle jest to opcjonalne) [afxoleregistertypelib —](../mfc/reference/registering-ole-controls.md#afxoleregistertypelib) funkcji znajduje się w tym celu. Poniższy przykład rejestruje bibliotekę typów francuskiego dla formantu ActiveX:  
  
 [!code-cpp[NVC_MFC_AxLoc#2](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_2.cpp)]  
  
 Po zarejestrowaniu kontroli nad `AfxOleRegisterTypeLib` funkcja automatycznie wyszukuje określony. TLB pliku w tym samym katalogu co kontrolki i rejestruje je w bazie danych rejestracji Windows. Jeśli. Nie można odnaleźć pliku TLB, funkcja nie ma wpływu.  
  
##  <a name="_core_localizing_the_control.92.s_user_interface"></a> Lokalizowanie formantu interfejsu użytkownika  
 Aby zlokalizować kontrolki interfejsu użytkownika, należy umieścić wszystkie kontrolki zasoby widoczny dla użytkownika (na przykład strony właściwości i komunikaty o błędach) do biblioteki DLL zasobów specyficznych dla języka. Następnie umożliwia właściwości identyfikator ustawień regionalnych kontenera wybierz odpowiedni plik DLL dla ustawień regionalnych użytkownika.  
  
 Poniższy przykład kodu demonstruje jedno z podejść do lokalizowania i ładowania biblioteki DLL zasobów dla określonych ustawień regionalnych. Ta funkcja elementu członkowskiego, wywoływana `GetLocalizedResourceHandle` w tym przykładzie, może być funkcją składową klasy kontrolki ActiveX:  
  
 [!code-cpp[NVC_MFC_AxLoc#3](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_3.cpp)]  
  
 Należy pamiętać, że identyfikator podjęzyk można sprawdzić w każdym przypadku instrukcji switch w celu zapewnienia bardziej wyspecjalizowane lokalizacji. Do pokazania tej funkcji, zobacz `GetResourceHandle` funkcji w MFC ActiveX kontroluje przykładowe [LOKALIZUJ](../visual-cpp-samples.md).  
  
 Gdy formant najpierw ładuje się w kontenerze, może wywołać [COleControl::AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid) można pobrać identyfikatora ustawień regionalnych. Kontrolki można następnie przekazać wartość Identyfikatora ustawień regionalnych zwrócone do `GetLocalizedResourceHandle` funkcji, która ładuje bibliotekę odpowiedniego zasobu. Formant należy przekazywać wynikowy uchwyt, aby [afxsetresourcehandle —](../mfc/reference/application-information-and-management.md#afxsetresourcehandle):  
  
 [!code-cpp[NVC_MFC_AxLoc#4](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_4.cpp)]  
  
 Przykładowy kod powyżej należy umieścić kontrolki, takie jak zastąpienie dla funkcji członkowskiej [COleControl::OnSetClientSite](../mfc/reference/colecontrol-class.md#onsetclientsite). Ponadto *m_hResDLL* powinien być zmienną składową klasy kontrolki.  
  
 Można używać podobnej logiki do lokalizowania strona właściwości formantu. Aby zlokalizować strony właściwości, należy dodać kod podobny do poniższego przykładu do pliku implementacji strony właściwości (w zastąpieniu obiektu [COlePropertyPage::OnSetPageSite](../mfc/reference/colepropertypage-class.md#onsetpagesite)):  
  
 [!code-cpp[NVC_MFC_AxLoc#5](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_5.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

