---
title: Kreator aplikacji Win32
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.win32.overview
helpviewer_keywords:
- Win32 Application Wizard
- Win32 Project Wizard
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
ms.openlocfilehash: 639834c8d723b65b894e6d216cbeb3b7f4dc37ec
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822694"
---
# <a name="win32-application-wizard"></a>Kreator aplikacji Win32

Kreatora aplikacji Win32 Visual C++ pozwala na tworzenie każdego z czterech typów projektów (wyszczególnionych w nagłówku w poniższej tabeli). W każdym przypadku można określić dodatkowe opcje, które są odpowiednie dla typu projektu, które można otworzyć. Poniższa tabela wskazuje, które opcje są dostępne dla każdego typu aplikacji.

|Typ obsługi|Aplikacja konsolowa|Aplikacja pliku wykonywalnego (Windows)|Biblioteka dołączana dynamicznie|Biblioteka statyczna|
|---------------------|-------------------------|----------------------------------------|---------------------------|--------------------|
|**Pusty projekt**|Tak|Yes|Yes|Nie|
|**Eksportuj symbole**|Nie|Nie|Yes|Nie|
|**Prekompilowany plik nagłówkowy**|Nie|Nie|Nie|Tak|
|**Obsługa biblioteki ATL**|Tak|Nie|Nie|Nie|
|**Obsługa MFC**|Tak|Nie|Nie|Tak|

## <a name="overview"></a>Omówienie

Ta strona kreatora opisuje bieżące ustawienia projektu dla aplikacji Win32, którą tworzysz. Domyślnie ustawiony są następujące opcje:

- Projekt jest w aplikacji Windows.

- Projekt nie jest pusty.

- Projekt nie zawiera symboli eksportu.

- Projekt nie korzysta z prekompilowanego pliku nagłówka (Ta opcja jest dostępna dla projektów biblioteki statycznej tylko).

- Projekt obejmuje obsługę MFC ani ATL.

Aby zmienić te ustawienia domyślne, kliknij przycisk [ustawienia aplikacji](../windows/application-settings-win-32-project-wizard.md) karty w lewej kolumnie kreatora i wprowadź żądane zmiany.

Po utworzeniu aplikacji pulpitu Windows można dodać ogólne klasy C++ za pomocą [ogólny](../ide/generic-cpp-class-wizard.md) kreatora kodów. Możesz dodać inne elementy, takie jak pliki HTML, pliki nagłówka, zasoby lub pliki tekstowe.

> [!NOTE]
> Nie można dodawać klas ALT, a klasy MFC można dodawać tylko do tych typów aplikacji klasycznych Windows, które obsługują MFC (zob. Poprzednia tabela).

Można wyświetlić pliki, Kreator tworzy projekt w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji o plikach, Kreator tworzy dla projektu, zobacz plik wygenerowany przez projekt `ReadMe.txt`. Aby uzyskać więcej informacji dotyczących typów plików [typy plików utworzonych dla projektów Visual C++](../build/reference/file-types-created-for-visual-cpp-projects.md).

## <a name="see-also"></a>Zobacz też

[Tworzenie pustej aplikacji klasycznej systemu Windows](../windows/creating-an-empty-windows-desktop-application.md)<br/>
[Typy projektów Visual C++](../build/reference/visual-cpp-project-types.md)