---
title: Szczegóły obsługi ATL dodanej przez kreatora ATL
ms.date: 08/20/2019
f1_keywords:
- vc.codewiz.atl.support
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
ms.openlocfilehash: 10bafc9bd06ee94398f91d5af478a6e1cd7ca617
ms.sourcegitcommit: bf1940a39029dbbd861f95480f55e5e8bd25cda0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2019
ms.locfileid: "70108453"
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>Szczegóły obsługi ATL dodanej przez kreatora ATL

::: moniker range=">=vs-2019"

Po dodaniu [obsługi ATL do istniejącego pliku wykonywalnego MFC lub dll](../../mfc/reference/adding-atl-support-to-your-mfc-project.md), program Visual Studio domyślnie dodaje plik nagłówka o nazwie *Framework. h* , `#define` który `#include` zawiera dyrektywy preprocesora, aby umożliwić korzystanie z ATL w projekcie. Nie dodano żadnych dodatkowych plików ani klas, jak zostało to zrobione w poprzednich wersjach programu Visual Studio.

::: moniker-end

::: moniker range="<=vs-2017"

Po [dodaniu obsługi ATL do istniejącego pliku wykonywalnego MFC lub dll](../../mfc/reference/adding-atl-support-to-your-mfc-project.md), Visual Studio wprowadza następujące zmiany do istniejącego projektu MFC (w tym przykładzie projekt jest wywoływany `MFCEXE`):

- Dodawane są dwa nowe pliki (plik. idl i plik. RGS służące do zarejestrowania serwera).

- W głównym pliku nagłówkowym i implementacji aplikacji (Mfcexe. h i Mfcexe. cpp) zostanie dodana nowa klasa (pochodna `CAtlMFCModule`od). Oprócz nowej klasy kod jest dodawany do `InitInstance` rejestracji. Kod jest również dodawany do `ExitInstance` funkcji do odwoływania obiektu klasy. W pliku nagłówkowym, na koniec, dwa nowe pliki nagłówkowe (Initguid. h i Mfcexe_i. c) są zawarte w pliku implementacji, deklarując i inicjując nowe identyfikatory GUID dla `CAtlMFCModule`klasy pochodnej.

- Aby zarejestrować serwer prawidłowo, wpis dla nowego pliku. RGS jest dodawany do pliku zasobów projektu.

::: moniker-end

## <a name="notes-for-dll-projects"></a>Uwagi dotyczące projektów bibliotek DLL

Po dodaniu obsługi ATL do projektu MFC DLL, pojawią się pewne różnice. Kod jest dodawany do `DLLRegisterServer` funkcji i `DLLUnregisterServer` w celu zarejestrowania i wyrejestrowania biblioteki DLL. Kod jest również dodawany do [DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow) i [DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject).

## <a name="see-also"></a>Zobacz także

[Obsługa ATL w projekcie MFC](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)<br/>
[Dodawanie funkcji za pomocą kreatorów kodu](../../ide/adding-functionality-with-code-wizards-cpp.md)<br/>
[Dodawanie klasy](../../ide/adding-a-class-visual-cpp.md)<br/>
[Dodawanie funkcji członkowskiej](../../ide/adding-a-member-function-visual-cpp.md)<br/>
[Dodawanie zmiennej członkowskiej](../../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Zastępowanie funkcji wirtualnej](../../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Procedura obsługi komunikatów MFC](../../mfc/reference/adding-an-mfc-message-handler.md)<br/>
[Nawigacja w strukturze klas](../../ide/navigate-code-cpp.md)
