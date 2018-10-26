---
title: Tworzenie projektu (ALT — samouczek, część 1) | Dokumentacja firmy Microsoft
ms.custom: get-started-article
ms.date: 09/26/2018
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
ms.openlocfilehash: 654ddd149eb6875bede85bdef51641c359644f51
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/25/2018
ms.locfileid: "50075635"
---
# <a name="creating-the-project-atl-tutorial-part-1"></a>Tworzenie projektu (ALT — Samouczek, część 1)

Ten samouczek zawiera instrukcje dotyczące nonattributed Projekt ATL, który tworzy obiekt ActiveX, który zawiera wielokąt. Obiekt zawiera opcje umożliwiające użytkownikowi, aby zmienić liczbę boków tworzących wielokąta i kod, aby odświeżyć wyświetlaną.

> [!NOTE]
> ATL i MFC nie są zazwyczaj obsługiwane w wersjach Express programu Visual Studio.

> [!NOTE]
> Ten samouczek tworzy ten sam kod źródłowy jako przykładowe wielokąta. Jeśli chcesz uniknąć ręcznego wprowadzania kodu źródłowego, możesz ją pobrać z [wielokąta przykładowy ogólny](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/Controls/Polygon). Możesz następnie można się odwoływać do kodu źródłowego wielokąta podczas pracy za pomocą tego samouczka lub używany w celu sprawdzenia błędów w własnego projektu.
> Aby skompilować, otwórz stdafx.h i Zastąp:
> ```
> #ifndef WINVER
> #define WINVER 0x0400
> #endif
> ```
> with
> ```
> #ifndef WINVER
> #define WINVER 0x0500
> #define _WIN32_WINNT 0x0500
> #endif
> ```
> Kompilator będzie nadal narzekają `regsvr32` nie zamykania poprawnie, ale nadal powinien mieć formantu biblioteki DLL, skompilowane i dostępne do użycia.

### <a name="to-create-the-initial-atl-project-using-the-atl-project-wizard"></a>Aby utworzyć początkową Projekt ATL za pomocą Kreatora projektu ATL

1. W środowisku programowania Visual Studio, kliknij przycisk **New** na **pliku** menu, a następnie kliknij przycisk **projektu**.

1. Otwórz **Visual C++** kartę, a następnie wybierz pozycję **MFC i ATL**. Wybierz **Projekt ATL**.

1. Typ *wielokąta* jako nazwę projektu.

    Lokalizację kodu źródłowego zwykle będą domyślnie \Users\\\<username > \source\repos i nowego folderu zostaną utworzone automatycznie.

1. Kliknij przycisk **OK** i **Projekt ATL** zostanie otwarty Kreator.

1. Kliknij przycisk **ustawienia aplikacji** Aby wyświetlić dostępne opcje.

1. Podczas tworzenia kontrolki i formantu musi być wewnątrz procesowego, pozostaw **typ aplikacji** jako biblioteki DLL.

1. Dla pozostałych opcji zostaw wartości domyślne, a następnie kliknij przycisk **OK**.

**Kreator projektów ATL** utworzy projekt przez wygenerowanie kilku plików. Można wyświetlić te pliki w **Eksploratora rozwiązań** , rozwijając `Polygon` obiektu. Pliki są wymienione poniżej.

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

1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `Polygon` projektu.

1. W menu skrótów kliknij **właściwości**.

1. Kliknij pozycję **konsolidatora**. Zmiana **na UserRedirection** opcję **tak**.

1. Kliknij przycisk **OK**.

W następnym kroku dodasz formant do projektu.

[Do kroku 2](../atl/adding-a-control-atl-tutorial-part-2.md)

## <a name="see-also"></a>Zobacz też

[Samouczek](../atl/active-template-library-atl-tutorial.md)
