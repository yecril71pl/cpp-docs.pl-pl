---
title: Kreator aplikacji Win32 | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.appwiz.win32.overview
dev_langs:
- C++
helpviewer_keywords:
- Win32 Application Wizard
- Win32 Project Wizard
ms.assetid: 5d7b3a5e-8461-479a-969a-67b7883725b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 18885e36b5f598a8b1dd6128c29a9e520128dcb2
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
---
# <a name="win32-application-wizard"></a>Kreator aplikacji Win32
Kreator aplikacji Win32 Visual C++ pozwala utworzyć cztery typy projektów (wymienione w pozycji w tabeli poniżej). W każdym przypadku można określić dodatkowe opcje, które są odpowiednie dla typu projektu, które będą otwierane. W poniższej tabeli przedstawiono opcje są dostępne dla każdego typu aplikacji.  
  
|Typ obsługi|Aplikacji konsoli|Aplikacja pliku wykonywalnego (system Windows)|Biblioteka DLL|Biblioteka statyczna|  
|---------------------|-------------------------|----------------------------------------|---------------------------|--------------------|  
|**Pusty projekt**|Tak|Tak|Tak|Nie|  
|**Eksportowanie symboli**|Nie|Nie|Tak|Nie|  
|**Prekompilowanego nagłówka**|Nie|Nie|Nie|Tak|  
|**Obsługa ATL**|Tak|Nie|Nie|Nie|  
|**Obsługa MFC**|Tak|Nie|Nie|Tak|  
  
## <a name="overview"></a>Omówienie  
 Ta strona kreatora opisano bieżące ustawienia projektu dla aplikacji Win32, które tworzysz. Domyślnie ustawione są następujące opcje:  
  
-   Projekt jest aplikacją systemu Windows.  
  
-   Projekt nie jest pusty.  
  
-   Projekt nie zawiera żadnych symboli eksportu.  
  
-   Projekt nie używa prekompilowanego pliku nagłówkowego (Ta opcja jest dostępna dla projektów biblioteki statycznej tylko).  
  
-   Projekt zawiera obsługę MFC ani ATL.  
  
 Aby zmienić te ustawienia domyślne, kliknij przycisk [ustawienia aplikacji](../windows/application-settings-win-32-project-wizard.md) w kolumnie po lewej stronie kreatora i wprowadź żądane zmiany.  
  
 Po utworzeniu aplikacji pulpitu systemu Windows, można dodać przy użyciu klasy C++ ogólne [ogólnego](../ide/generic-cpp-class-wizard.md) kodu kreatora. Można dodać inne elementy, takie jak pliki HTML, pliki nagłówkowe, zasobów lub plików tekstowych.  
  
> [!NOTE]
>  Nie można dodać klasy ATL i MFC — klasy można dodać tylko do tych typów aplikacji klasycznych systemu Windows, które obsługują MFC (zobacz poprzedniej tabeli).  
  
 Kreator tworzy pliki można wyświetlić dla projektu w **Eksploratora rozwiązań**. Aby uzyskać więcej informacji o plikach Kreator tworzy dla projektu można znaleźć w pliku wygenerowanego projektu ReadMe.txt. Aby uzyskać więcej informacji na temat typów plików [pliku typy utworzone dla projektów Visual C++](../ide/file-types-created-for-visual-cpp-projects.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Tworzenie aplikacji klasycznych pusty systemu Windows](../windows/creating-an-empty-windows-desktop-application.md)   
 [Typy projektów Visual C++](../ide/visual-cpp-project-types.md)