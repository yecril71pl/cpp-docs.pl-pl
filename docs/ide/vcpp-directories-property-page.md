---
title: "Strona właściwości katalogów VC ++ | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCDirectories.IncludePath
- VC.Project.VCDirectories.ReferencePath
- VC.Project.VCDirectories.SourcePath
- VC.Project.VCDirectories.LibraryWPath
- VC.Project.VCDirectories.ExecutablePath
- VC.Project.VCDirectories.LibraryPath
- VS.ToolsOptionsPages.Projects.VCDirectories
- VC.Project.VCDirectories.ExcludePath
dev_langs: C++
helpviewer_keywords: VC++ Directories Property Page
ms.assetid: 428eeef6-f127-4271-b3ea-0ae6f2c3d624
caps.latest.revision: "25"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 30a54b1d90585e6433f059acf30991ca53948d60
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="vc-directories-property-page"></a>Strona właściwości katalogów VC++
Określa katalogi, których Visual Studio ma używać podczas tworzenia projektu. Uzyskiwanie dostępu do tej strony właściwości w **Eksploratora rozwiązań**, otwórz menu skrótów projektu i wybierz polecenie **właściwości**, a następnie w okienku po lewej stronie z **strony właściwości** okno dialogowe rozwiń **właściwości konfiguracji** i wybierz **katalogi VC ++**.  
  
 Gdy używasz Visual Studio do tworzenia projektu, dziedziczy on niektóre katalogi. Wiele z nich jest wyrażonych za pomocą makra. Aby sprawdzić bieżącą wartość makra, w prawym okienku **katalogi VC ++** wybierz wiersz — na przykład **katalogi dołączenia**— wybierz przycisk strzałki w dół po prawej stronie, wybierz  **Edytuj**, a następnie w oknie dialogowym wybierz **makra** przycisku. Aby uzyskać więcej informacji, zobacz wpisy na blogu: [katalogi VC ++](http://blogs.msdn.com/b/vsproject/archive/2009/07/07/vc-directories.aspx), [właściwości dziedziczone i arkusze właściwości](http://blogs.msdn.com/b/vsproject/archive/2009/06/23/inherited-properties-and-property-sheets.aspx), i [programu Visual Studio 2010 C++ projektu przewodnik uaktualniania](http://blogs.msdn.com/b/vcblog/archive/2010/03/02/visual-studio-2010-c-project-upgrade-guide.aspx).  
  
## <a name="directory-types"></a>Typy katalogów  
 Można również określić inne katalogi, jak poniżej.  
  
 **Katalogi plików wykonywalnych**  
 Katalogi, w których należy szukać plików wykonywalnych. Odpowiada **ścieżki** zmiennej środowiskowej.  
  
 **Dołącz katalogi**  
 Katalogi, w których należy szukać dołączanych plików, do których istnieją odwołania w kodzie źródłowym. Odpowiada **INCLUDE** zmiennej środowiskowej.  
  
 **Odwołanie do katalogów**  
 Katalogi wyszukiwania zestawów i modułów (metadanymi) pliki, których istnieją odwołania w kodzie źródłowym przez [#using](../preprocessor/hash-using-directive-cpp.md) dyrektywy. Odpowiada **LIBPATH** zmiennej środowiskowej.  
  
 **Katalogi bibliotek**  
 Katalogi, w których należy szukać plików biblioteki (.lib); obejmują biblioteki wykonywalne. Odpowiada **LIB** zmiennej środowiskowej. To ustawienie nie ma zastosowania do plików .obj; Aby utworzyć łącze do pliku .obj na [konsolidatora](../ide/linker-property-pages.md)**ogólne** strony właściwości, wybierz opcję **dodatkowe zależności biblioteki** , a następnie określ ścieżkę względną pliku.  
  
 **Katalogi źródłowe**  
 Katalogi, w których należy szukać plików źródłowych dla technologii IntelliSense.  
  
 **Wyklucz katalogi**  
 Katalogi, których nie należy przeszukiwać podczas sprawdzania zależności kompilacji.  
  
#### <a name="to-specify-or-modify-directory-settings"></a>Aby określić lub zmodyfikować ustawienia katalogu  
  
1.  W **Eksploratora rozwiązań**, otwórz menu skrótów projektu chcesz zmienić, a następnie wybierz pozycję **właściwości**.  
  
2.  W lewym okienku **strony właściwości** okna dialogowego rozwiń **właściwości konfiguracji** , a następnie wybierz **katalogi VC ++**.  
  
3.  Aby zmodyfikować jedną listę katalogów, zaznacz go, kliknij przycisk strzałki w dół po prawej stronie, a następnie wybierz **Edytuj**.  
  
     W polu w wyświetlonym oknie dialogowym można dodać lub usunąć wartości i można zmienić kolejność wyświetlania wartości. Można również określić, czy projekt dziedziczy wszystkie ustawienia, zaznaczając lub usuwając **Dziedzicz po elemencie nadrzędnym lub domyślnych wartościach projektu**.  
  
## <a name="sharing-the-settings"></a>Współdzielenie ustawień  
 Właściwości projektu można udostępniać innym użytkownikom lub na wielu komputerach. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../ide/working-with-project-properties.md).  
  
