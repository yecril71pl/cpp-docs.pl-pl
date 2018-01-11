---
title: "Tworzenie projektu (ALT — samouczek, część 1) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: get-started-article
dev_langs: C++
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1a9a5fc9a0d2175a419bbc0fb1aacbc9ea25006c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>Tworzenie projektu (ALT — Samouczek, część 1)
Ten samouczek przedstawia instrukcje dotyczące nonattributed Projekt ATL, który tworzy obiekt ActiveX, który wyświetla wielokąta. Obiekt zawiera opcje dzięki czemu użytkownik Aby zmienić liczbę stron tworzących wielokąt i kod odświeżyć ekran.  
  
> [!NOTE]
>  ATL i MFC nie są zwykle obsługiwane w wersji Express programu Visual Studio.  
  
> [!NOTE]
>  W tym samouczku tworzy ten sam kod źródłowy jako przykład wielokąta. Jeśli chcesz uniknąć ręczne wprowadzenie kodu źródłowego, możesz pobrać go z [wielokąta przykładowy ogólny](../visual-cpp-samples.md). Następnie może dotyczyć wielokąta kodu źródłowego, jak pracy przewodnik, lub użyj go, aby sprawdzić błędy w własnego projektu.  
  
### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>Aby utworzyć Projekt ATL początkowej służy Kreator projektu ATL  
  
1.  W środowisku projektowym Visual Studio, kliknij przycisk **nowy** na **pliku** menu, a następnie kliknij przycisk **projektu**.  
  
2.  Kliknij przycisk **projekty Visual C++** i wybierz polecenie **Projekt ATL**.  
  
3.  Typ `Polygon` z nazwą projektu.  
  
     Będzie domyślną lokalizację kodu źródłowego Moje projekty Studio Documents\Visual, a nowy folder zostaną utworzone automatycznie.  
  
4.  Kliknij przycisk **OK** i zostanie otwarty Kreator projektu ATL.  
  
5.  Kliknij przycisk **ustawienia aplikacji** Aby wyświetlić dostępne opcje.  
  
6.  Tworzysz formantu i formantu musi być server wewnątrzprocesowe, pozostaw **typu aplikacji** jako biblioteki DLL.  
  
7.  Pozostaw wartości domyślne inne opcje, a następnie kliknij przycisk **Zakończ**.  
  
 Kreator projektu ATL utworzy projekt, generując kilka plików. Pliki te można wyświetlić w Eksploratorze rozwiązań, rozwijając obiektu wielokąta. Pliki są wymienione poniżej.  
  
|Plik|Opis|  
|----------|-----------------|  
|Polygon.cpp|Zawiera implementację `DllMain`, `DllCanUnloadNow`, `DllGetClassObject`, `DllRegisterServer`, i `DllUnregisterServer`. Zawiera także mapa obiektów, czyli listę obiektów ATL w projekcie. To jest początkowo pusta.|  
|Polygon.def|Ten plik definicji modułu zawiera konsolidatora z informacjami o eksportuje wymagane przez biblioteki DLL.|  
|Polygon.IDL|Plik języka definicji interfejsu, który opisuje interfejsy specyficzne dla obiektów.|  
|Polygon.rgs|Ten skrypt rejestru zawiera informacje dotyczące rejestrowania programu biblioteki DLL.|  
|Polygon.RC|Plik zasobu, który początkowo zawiera informacje o wersji i ciąg zawierający nazwę projektu.|  
|Resource.h|Plik nagłówka pliku zasobu.|  
|Polygonps.def|Ten plik definicji modułu zawiera konsolidatora z informacjami o eksportuje wymagane przez kod serwera proxy i skrótowych obsługujących wywołania w apartamentach.|  
|stdafx.cpp|Plik, który będzie `#include` ATL plików implementacji.|  
|stdafx.h|Plik, który będzie `#include` ATL pliki nagłówków.|  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy `Polygon` projektu.  
  
2.  W menu skrótów kliknij **właściwości**.  
  
3.  Polecenie **konsolidatora**. Zmień **na UserRedirection** opcji w celu **tak**.  
  
4.  Kliknij przycisk **OK**.  
  
 W następnym kroku formantu zostaną dodane do projektu.  
  
 [Do kroku 2](../atl/adding-a-control-atl-tutorial-part-2.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek](../atl/active-template-library-atl-tutorial.md)

