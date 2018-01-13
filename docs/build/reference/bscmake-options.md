---
title: Opcje BSCMAKE | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCBscMakeTool.OutputFile
- VC.Project.VCBscMakeTool.SuppressStartupBanner
- VC.Project.VCBscMakeTool.PreserveSBR
dev_langs: C++
helpviewer_keywords:
- /v BSCMAKE option
- Iu BSCMAKE option
- browse information files (.bsc), content
- /Er BSCMAKE option
- NOLOGO BSCMAKE option
- /s BSCMAKE option
- /Ei BSCMAKE option
- /o BSCMAKE option
- /NOLOGO BSCMAKE option
- /Iu BSCMAKE option
- s BSCMAKE option (/s)
- /Em BSCMAKE option
- Em BSCMAKE option
- Es BSCMAKE option
- files [C++], BSCMAKE
- Er BSCMAKE option
- BSCMAKE, options for controlling files
- controlling BSCMAKE options
- El BSCMAKE option
- /El BSCMAKE option
- /Es BSCMAKE option
- Ei BSCMAKE option
ms.assetid: fa2f1e06-c684-41cf-80dd-6a554835ebd2
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 46c258a5591615bb277823ccc5261fade3c5e2af
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="bscmake-options"></a>Opcje BSCMAKE
W tej sekcji opisano dostępne kontrolowanie BSCMAKE opcje. Kilka opcji kontrolować zawartość pliku informacyjnego przeglądarki, z wyłączeniem lub w tym informacje o niektórych. Opcje wykluczeń można zezwolić na BSCMAKE do szybsze i może spowodować mniejszy plik .bsc. Opcja nazwy jest uwzględniana wielkość liter (z wyjątkiem **/HELP** i **/nologo**).  
  
 Tylko **/nologo** i **/o** są dostępne w środowisku programowania Visual Studio.  Zobacz [Ustawianie właściwości projektu Visual C++](../../ide/working-with-project-properties.md) informacji na dostęp do strony właściwości projektu.  
  
 /EI ( `filename`...)  
 Wyklucza zawartość określonego Dołącz pliki z pliku informacyjnego przeglądarki. Aby określić wiele plików, Rozdziel ich nazwy spacjami i ująć listę w nawiasach. Nawiasy nie są konieczne, jeśli można określić tylko jeden `filename`. Użyj **/Ei** wraz z **/Es** opcji, aby wykluczyć pliki nie zostały wyłączone przez **/Es**.  
  
 /EL  
 Wyklucza symbole lokalne. Wartość domyślna to dołączać symbole lokalne. Aby uzyskać więcej informacji na temat symbole lokalne, zobacz [Tworzenie pliku .sbr](../../build/reference/creating-an-dot-sbr-file.md).  
  
 /Em  
 Wyklucza symbole w treści makra. Użyj **/Em** do uwzględnienia tylko nazwy makra w pliku informacyjnego przeglądarki. Wartość domyślna to zarówno nazwy makr i wynik rozwinięcia makra są.  
  
 /ER ( `symbol`...)  
 Wyłącza określony symbole z pliku informacyjnego przeglądarki. Aby określić wiele nazw symboli, Rozdziel ich nazwy spacjami i ująć listę w nawiasach. Nawiasy nie są konieczne, jeśli można określić tylko jeden `symbol`.  
  
 /ES  
 Wyklucza z pliku informacyjnego przeglądarki każdego pliku dołączanego określona za pomocą ścieżki bezwzględnej lub znaleziony w określone w zmiennej środowiskowej INCLUDE ścieżkę bezwzględną. (Zazwyczaj są to system zawierać pliki, które zawierają wiele informacji, które nie mogą być potrzebne w pliku informacji o przeglądaniu.) Ta opcja nie wyklucza określono bez ścieżki lub za pomocą ścieżek względnych lub pliki znajdujące się w ścieżki względnej DOŁĄCZANIA plików. Można użyć **/Ei** opcji wraz z **/Es** Aby wykluczyć pliki **/Es** nie wyklucza. Jeśli chcesz wykluczyć tylko niektóre pliki który **/Es** wyklucza, użyj **/Ei** zamiast **/Es** i wyświetlić listę plików, które chcesz wykluczyć.  
  
 / errorreport: [Brak &#124; wiersz &#124; kolejki &#124; wysyłania]  
 Umożliwia wysyłanie informacji do firmy Microsoft dotyczące błędy wewnętrzne w bscmake.exe.  
  
 Aby uzyskać więcej informacji na temat **/errorreport**, zobacz [/errorreport (zgłaszaj wewnętrzne błędy kompilatora)](../../build/reference/errorreport-report-internal-compiler-errors.md).  
  
 / HELP  
 Wyświetla podsumowanie składni wiersza polecenia BSCMAKE.  
  
 /IU  
 Zawiera symbole bez odwołań. Domyślnie BSCMAKE nie obsługuje żadnych symboli, które są zdefiniowane, ale nie odwołuje się do. Jeśli pakowane pliku .sbr tej opcji nie ma wpływu na tego pliku wejściowego kompilator został już usunięty nieużywane symboli.  
  
 /n  
 Wymusza nieprzyrostowa kompilacji. Użyj  **/n**  Aby wymusić pełne kompilacji pliku informacyjnego przeglądarki, czy istnieje plik .bsc i aby zapobiec obcinania plików SBR. Zobacz [sposób BSCMAKE kompiluje plik .bsc](../../build/reference/how-bscmake-builds-a-dot-bsc-file.md).  
  
 /NOLOGO  
 Pomija komunikat o prawach autorskich BSCMAKE.  
  
 /o`filename`  
 Określa nazwę pliku informacyjnego przeglądarki. Domyślnie BSCMAKE daje pliku informacyjnego przeglądarki z podstawowej nazwy pierwszy plik SBR i rozszerzenia .bsc.  
  
 /S ( `filename`...)  
 Określa, że BSCMAKE do przetworzenia pliku dołączanego określona po raz pierwszy jest napotkała i do wykluczenia w inny sposób. Użyj tej opcji, aby skrócić czas przetwarzania po pliku (np. nagłówek lub .h, pliku dla plików .c lub .cpp pliku źródłowego) znajduje się w kilku plików źródłowych, ale nie ma wpływu dyrektywy przetwarzania wstępnego zawsze. Można także użyć tej opcji, jeśli plik zostanie zmieniona w sposób, w którym nie są ważne dla pliku informacyjnego przeglądarki, które tworzysz. Aby określić wiele plików, Rozdziel ich nazwy spacjami i ująć listę w nawiasach. Nawiasy nie są konieczne, jeśli można określić tylko jeden `filename`. Jeśli chcesz wykluczyć pliku za każdym razem, gdy jest dostępna, należy użyć **/Ei** lub **/Es** opcji.  
  
 /v  
 Zapewnia pełne dane wyjściowe, w tym nazwy poszczególnych plików SBR, przetwarzanych i informacje o BSCMAKE ukończone, uruchom.  
  
 /?  
 Wyświetla krótki opis składni wiersza polecenia BSCMAKE.  
  
 Następujące polecenie w wierszu informuje BSCMAKE przeprowadzenie pełnej kompilacji MAIN.bsc z trzech plików SBR. Ponadto informuje BSCMAKE do wykluczenia zduplikowane wystąpienia TOOLBOX.h:  
  
```  
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr  
```  
  
## <a name="see-also"></a>Zobacz też  
 [BSCMAKE — dokumentacja](../../build/reference/bscmake-reference.md)