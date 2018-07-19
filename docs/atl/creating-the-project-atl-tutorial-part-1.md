---
title: Tworzenie projektu (ALT — samouczek, część 1) | Dokumentacja firmy Microsoft
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1906ac1ae8c1e526d78690e131a7ca5147283d76
ms.sourcegitcommit: 76fd30ff3e0352e2206460503b61f45897e60e4f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/13/2018
ms.locfileid: "39025929"
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>Tworzenie projektu (ALT — Samouczek, część 1)
Ten samouczek zawiera instrukcje dotyczące nonattributed Projekt ATL, który tworzy obiekt ActiveX, który zawiera wielokąt. Obiekt zawiera opcje umożliwiające użytkownikowi, aby zmienić liczbę boków tworzących wielokąta i kod, aby odświeżyć wyświetlaną.  
  
> [!NOTE]
>  ATL i MFC nie są zazwyczaj obsługiwane w wersjach Express programu Visual Studio.  
  
> [!NOTE]
>  Ten samouczek tworzy ten sam kod źródłowy jako przykładowe wielokąta. Jeśli chcesz uniknąć ręcznego wprowadzania kodu źródłowego, możesz ją pobrać z [wielokąta przykładowy ogólny](../visual-cpp-samples.md). Możesz następnie można się odwoływać do kodu źródłowego wielokąta podczas pracy za pomocą tego samouczka lub używany w celu sprawdzenia błędów w własnego projektu.  
  
### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>Aby utworzyć początkową Projekt ATL za pomocą Kreatora projektu ATL  
  
1.  W środowisku programowania Visual Studio, kliknij przycisk **New** na **pliku** menu, a następnie kliknij przycisk **projektu**.  
  
2.  Kliknij przycisk **projekty języka Visual C++** i wybierz polecenie **Projekt ATL**.  
  
3.  Typ *wielokąta* jako nazwę projektu.  
  
     My Documents\Visual Studio projekty zazwyczaj domyślnie lokalizacji kodu źródłowego, a nowy folder zostaną utworzone automatycznie.  
  
4.  Kliknij przycisk **OK** i zostanie otwarty Kreator projektów ATL.  
  
5.  Kliknij przycisk **ustawienia aplikacji** Aby wyświetlić dostępne opcje.  
  
6.  Podczas tworzenia kontrolki i formantu musi być wewnątrz procesowego, pozostaw **typ aplikacji** jako biblioteki DLL.  
  
7.  Dla pozostałych opcji zostaw wartości domyślne, a następnie kliknij przycisk **Zakończ**.  
  
 Kreator projektu ATL utworzy projekt przez wygenerowanie kilku plików. Pliki te można wyświetlić w Eksploratorze rozwiązań, rozwijając obiektu wielokąta. Pliki są wymienione poniżej.  
  
    |Plik|Opis|  
    |----------|-----------------|  
    |Polygon.cpp|Zawiera implementację `DllMain`, `DllCanUnloadNow`, `DllGetClassObject`, `DllRegisterServer`, i `DllUnregisterServer`. Zawiera także na mapie obiektu, który znajduje się lista obiektów ATL w projekcie. To jest początkowo pusta.|  
    |Polygon.def|Ten plik definicji modułu zawiera konsolidatora z informacjami o eksporty wymagane przez bibliotekę DLL.|  
    |Polygon.IDL|Plik języka definicji interfejsu, opisujący interfejsy specyficzne dla obiektów.|  
    |Polygon.rgs|Ten skrypt rejestru zawiera informacje dotyczące rejestrowania biblioteki DLL programu.|  
    |Polygon.RC|Plik zasobów początkowo zawiera informacje o wersji i ciąg zawierający nazwę projektu.|  
    |Resource.h|Plik nagłówka dla pliku zasobów.|  
    |Polygonps.def|Ten plik definicji modułu zawiera program łączący się z informacjami o informacje o operacjach eksportowania wymagane przez serwer proxy i szkieletu kodu, które obsługują wywołania w apartamentach.|  
    |stdafx.cpp|Plik który będzie `#include` ATL pliki wdrożenia.|  
    |stdafx.h|Plik który będzie `#include` plików nagłówkowych ATL.|  
  
1.  W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy `Polygon` projektu.  
  
2.  W menu skrótów kliknij **właściwości**.  
  
3.  Kliknij pozycję **konsolidatora**. Zmiana **na UserRedirection** opcję **tak**.  
  
4.  Kliknij przycisk **OK**.  
  
 W następnym kroku dodasz formant do projektu.  
  
 [Do kroku 2](../atl/adding-a-control-atl-tutorial-part-2.md)  
  
## <a name="see-also"></a>Zobacz też  
 [Samouczek](../atl/active-template-library-atl-tutorial.md)

