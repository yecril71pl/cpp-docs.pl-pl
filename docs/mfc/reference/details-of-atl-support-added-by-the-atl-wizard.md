---
title: Szczegóły obsługi ATL dodanej przez kreatora ATL
ms.date: 11/04/2016
f1_keywords:
- vc.codewiz.atl.support
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
ms.openlocfilehash: 2651a83c50b03dfffd1ac0238b6c6d0a61888c88
ms.sourcegitcommit: 65ed563a8a1d4d90f872a2a6edcb086f84ec9f77
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2019
ms.locfileid: "66741557"
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>Szczegóły obsługi ATL dodanej przez kreatora ATL

Po użytkownik [Dodaj obsługę ATL do istniejącego pliku DLL lub pliku wykonywalnego MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md), następujących modyfikacji istniejącego projektu MFC sprawia, że Visual C++ (w tym przykładzie projekt nosi `MFCEXE`):

- Dwa nowe pliki (pliku .idl i pliku .rgs, używanego do zarejestrowania serwera) są dodawane.

- W głównym nagłówkowy i implementacji pliki aplikacji (Mfcexe.h i Mfcexe.cpp) nowej klasy (pochodną `CAtlMFCModule`) zostanie dodany. Oprócz nowej klasy, kod jest dodawany do `InitInstance` rejestracji. Kod jest także dodawane do `ExitInstance` funkcja odwołać obiektu klasy. W pliku nagłówkowym, na koniec dwa nowe pliki nagłówkowe (Initguid.h i Mfcexe_i.c) znajdują się w pliku implementacji, deklarowania i inicjowania nowych identyfikatorów GUID dla `CAtlMFCModule`-klasy pochodnej.

- Aby zarejestrować serwer poprawnie, wpis dla nowego pliku .rgs jest dodawany do projektu pliku zasobów.

## <a name="notes-for-dll-projects"></a>Uwagi dla projektów biblioteki DLL

Po dodaniu obsługi ATL do projektu MFC DLL, zobaczą pewne różnice. Kod jest dodawany do `DLLRegisterServer` i `DLLUnregisterServer` funkcje rejestrowania i wyrejestrowania biblioteki DLL. Kod jest także dodawane do [DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow) i [DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject).

## <a name="see-also"></a>Zobacz także

[Obsługa ATL w projekcie MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Dodawanie funkcji członkowskiej](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Dodawanie zmiennej członkowskiej](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Zastępowanie funkcji wirtualnych](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Handler komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Nawigacja w strukturze klas](../../ide/navigate-code-cpp.md)
