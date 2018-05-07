---
title: 'Formanty MFC ActiveX: Lokalizowanie formantu ActiveX | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: afe134b4acdcea3ec5f1a6ce381be0ca10c321d8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="mfc-activex-controls-localizing-an-activex-control"></a>Kontrolki ActiveX MFC: lokalizowanie kontrolki ActiveX
W tym artykule omówiono procedury lokalizowanie interfejsy formantu ActiveX.  
  
 Jeśli chcesz dostosować formantu ActiveX na rynek międzynarodowe, warto lokalizowanie formantu. System Windows obsługuje wiele języków innych niż angielski, niemiecki, francuski i szwedzki w tym domyślny. Jeśli interfejs jest tylko w języku angielskim może stanowić problemów dla formantu.  
  
 Ogólnie rzecz biorąc kontrolek ActiveX zawsze należy oprzeć ich ustawień regionalnych na właściwość otoczenia identyfikator ustawień regionalnych. Istnieją trzy sposoby, w tym:  
  
-   Ładowanie zasobów zawsze na żądanie, w oparciu o bieżące wartości właściwości otoczenia identyfikator ustawień regionalnych. Przykładowe kontrolki MFC ActiveX [LOKALIZUJ](../visual-cpp-samples.md) używa tej strategii.  
  
-   Ładowanie zasobów podczas instancji pierwszą kontrolkę, na podstawie właściwości otoczenia identyfikator ustawień regionalnych i używać tych zasobów dla innych wystąpień. W tym artykule przedstawiono tej strategii.  
  
    > [!NOTE]
    >  To nie będzie działać prawidłowo w niektórych przypadkach, jeśli przyszłych wystąpienia mają różne ustawienia regionalne.  
  
-   Użyj **OnAmbientChanged** funkcji powiadomień, aby załadować dynamicznie do odpowiednich zasobów dla ustawień regionalnych kontenera.  
  
    > [!NOTE]
    >  To będzie działać dla formantu, ale biblioteki DLL środowiska wykonawczego nie dynamicznie zaktualizuje własnych zasobów po zmianie właściwości otoczenia identyfikator ustawień regionalnych. Ponadto biblioteki DLL środowiska wykonawczego dla formantów ActiveX umożliwia określenie, ustawienia regionalne dla swoich zasobów ustawienia regionalne wątku.  
  
 Dalszej części tego artykułu opisano dwa strategie lokalizowanie. Pierwszy strategii [lokalizuje interfejs programowania formantu](#_core_localizing_your_control.92.s_programmability_interface) (nazwy właściwości, metod i zdarzeń). Drugi strategii [lokalizuje formantu interfejsu użytkownika](#_core_localizing_the_control.92.s_user_interface), za pomocą właściwości LocaleID kontenera. Próbka formantów MFC ActiveX dla pokaz lokalizacji kontrolki [LOKALIZUJ](../visual-cpp-samples.md).  
  
##  <a name="_core_localizing_your_control.92.s_programmability_interface"></a> Lokalizowanie formantu interfejsu programowania  
 Lokalizowanie formantu interfejsu programowania (interfejs używane przez programistów pisania aplikacji, które Użyj swojego formantu), należy utworzyć zmodyfikowanej wersji formantu. IDL pliku (skrypt do tworzenia biblioteki typu formantu) dla każdego języka, który ma obsługiwać. Jest to tylko miejsce potrzebne do zlokalizowania nazw właściwości formantu.  
  
 Podczas opracowywania zlokalizowanych formantu zawierać identyfikator ustawień regionalnych jako atrybut na poziomie biblioteki typów. Na przykład jeśli chcesz udostępnić francuskim zlokalizowanej właściwości nazwy biblioteki typów, należy utworzyć kopię PRZYKŁADU. IDL pliku i wywołują go SAMPLEFR. IDL. Dodaj atrybut Identyfikator ustawień regionalnych do pliku (identyfikator ustawień regionalnych francuski jest 0x040c), podobny do następującego:  
  
 [!code-cpp[NVC_MFC_AxLoc#1](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_1.idl)]  
  
 Zmień nazwy właściwości w SAMPLEFR. IDL, aby ich odpowiedniki francuskim, a następnie użyć mktyplib —. EXE w celu utworzenia francuskiego typu biblioteki, SAMPLEFR. TLB.  
  
 Aby utworzyć wiele bibliotek typów zlokalizowanych można dodać zlokalizowane. IDL, pliki do projektu i zostaną one automatycznie skompilowane.  
  
#### <a name="to-add-an-idl-file-to-your-activex-control-project"></a>Aby dodać. Plik IDL do projektu formantu ActiveX  
  
1.  Otwarty na projektu kontroli **projektu** menu, kliknij przycisk **Dodaj istniejący element**.  
  
     **Dodaj istniejący element** zostanie wyświetlone okno dialogowe.  
  
2.  W razie potrzeby wybierz dysk i katalog, aby wyświetlić.  
  
3.  W **pliki typu** wybierz opcję **wszystkie pliki (\*.\*)** .  
  
4.  W polu listy plików kliknij dwukrotnie. Plik IDL, który chcesz wstawić do projektu.  
  
5.  Kliknij przycisk **Otwórz** po dodaniu wszystkie niezbędne. IDL, pliki.  
  
 Ponieważ pliki zostały dodane do projektu, będzie można kompilować w jest oparta pozostała część projektu. Biblioteki typów zlokalizowanych znajdują się w bieżącym katalogu projektu formantu ActiveX.  
  
 W kodzie nazwy właściwości wewnętrzny (zazwyczaj w języku angielskim) są zawsze używane i nigdy nie są zlokalizowane. W tym mapy wysyłania formantów, funkcje wymiany właściwości i kodu wymiany danych strony właściwości.  
  
 Tylko jeden typ biblioteki (. Plik TLB) może zostać powiązane do zasobów z implementacją kontrolki (. Plik OCX). Zazwyczaj jest to wersja z znormalizowanych (zazwyczaj angielski) nazwy. Na potrzeby wysłania zlokalizowanej wersji musisz wysłać formantu. OCX (która jest już powiązane domyślne. Wersja biblioteki TLB) i. TLB dla odpowiednich ustawień regionalnych. Oznacza to, że tylko. OCX jest wymagany dla angielskiej wersji, ponieważ poprawny. TLB jest już powiązane do niego. Dla innych ustawień regionalnych biblioteki typów zlokalizowanych również muszą być wysłane z. OCX.  
  
 Aby upewnić się, że klienci formantu można znaleźć biblioteki typów zlokalizowanego, zarejestruj ustawień regionalnych. TLB plików w sekcji biblioteki typów w rejestrze systemu Windows. Trzeci parametr (zwykle jest to opcjonalne) [afxoleregistertypelib —](../mfc/reference/registering-ole-controls.md#afxoleregistertypelib) funkcji znajduje się w tym celu. Poniższy przykład rejestruje francuskim typu biblioteki dla formantów ActiveX:  
  
 [!code-cpp[NVC_MFC_AxLoc#2](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_2.cpp)]  
  
 Po zarejestrowaniu formantu `AfxOleRegisterTypeLib` funkcja automatycznie wyszukuje określony. TLB pliku w tym samym katalogu co formantu i rejestruje go w bazie danych rejestracji systemu Windows. Jeśli. Nie znaleziono pliku TLB, funkcja nie ma wpływu.  
  
##  <a name="_core_localizing_the_control.92.s_user_interface"></a> Lokalizowanie formantu interfejsu użytkownika  
 Do zlokalizowania formantu interfejsu użytkownika, umieść wszystkie kontrolki zasoby widoczny dla użytkownika (np. strony właściwości i komunikaty o błędach) do biblioteki DLL zasobów specyficzne dla języka. Można następnie użyć kontenera otoczenia identyfikator ustawień regionalnych właściwości zaznacz odpowiednie biblioteki DLL dla ustawień regionalnych użytkownika.  
  
 Poniższy przykład kodu pokazuje jednym z podejść do lokalizowania i ładowania biblioteki DLL zasobów dla określonych ustawień regionalnych. Funkcji członkowskiej, nazywany `GetLocalizedResourceHandle` na przykład może być funkcją członkowską klasy formantu ActiveX:  
  
 [!code-cpp[NVC_MFC_AxLoc#3](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_3.cpp)]  
  
 Należy pamiętać, że identyfikator odmianą języka można sprawdzić w każdym przypadku instrukcji switch, aby zapewnić wyspecjalizowanego lokalizacji. Aby demonstracyjne tej funkcji, zobacz `GetResourceHandle` funkcji w MFC ActiveX określa próbki [LOKALIZUJ](../visual-cpp-samples.md).  
  
 Gdy kontrolka najpierw ładuje się do kontenera, może wywołać [COleControl::AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid) można pobrać identyfikatora ustawień regionalnych. Kontrolki można następnie przekazać wartość Identyfikatora ustawień regionalnych zwrócony do `GetLocalizedResourceHandle` funkcja, która ładuje bibliotekę prawidłowego zasobu. Kontrolki powinno przekazać uchwytu wynikowy, do [afxsetresourcehandle —](../mfc/reference/application-information-and-management.md#afxsetresourcehandle):  
  
 [!code-cpp[NVC_MFC_AxLoc#4](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_4.cpp)]  
  
 Umieść powyższy kod przykładowy w funkcji członkowskiej klasy formantu, takie jak zastępująca [COleControl::OnSetClientSite](../mfc/reference/colecontrol-class.md#onsetclientsite). Ponadto `m_hResDLL` powinien być zmienną członkowską klasy formantu.  
  
 Podobne logiki służącego do lokalizowania strony właściwości formantu. Do zlokalizowania strony właściwości, należy dodać kod podobny do poniższego przykładu do pliku implementacji strony właściwości (w zastępująca [COlePropertyPage::OnSetPageSite](../mfc/reference/colepropertypage-class.md#onsetpagesite)):  
  
 [!code-cpp[NVC_MFC_AxLoc#5](../mfc/codesnippet/cpp/mfc-activex-controls-localizing-an-activex-control_5.cpp)]  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki ActiveX MFC](../mfc/mfc-activex-controls.md)

