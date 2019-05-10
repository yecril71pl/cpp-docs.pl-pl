---
title: Tworzenie projektu (ALT — Samouczek, część 1)
ms.custom: get-started-article
ms.date: 05/06/2019
ms.assetid: f6b727d1-390a-4b27-b82f-daadcd9fc059
ms.openlocfilehash: 292faf1769baa2e1c3fc6e52ba6df065cf08766e
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221408"
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

1. W programie Visual Studio 2017 i starszych wersji: **Plik** > **nowe** > **projektu**. Otwórz **Visual C++**  kartę, a następnie wybierz pozycję **MFC i ATL**. Wybierz **Projekt ATL**.

   In Visual Studio 2019: Wybierz **pliku** > **New** > **projektu**, w polu wyszukiwania wpisz "ALT" i wybierz **Projekt ATL**.

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
|Polygon.rc|Plik zasobów początkowo zawiera informacje o wersji i ciąg zawierający nazwę projektu.|
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

## <a name="see-also"></a>Zobacz także

[Samouczek](../atl/active-template-library-atl-tutorial.md)
