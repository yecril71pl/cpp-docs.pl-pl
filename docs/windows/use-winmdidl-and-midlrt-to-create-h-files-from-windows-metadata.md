---
title: 'Porady: Użyj winmdidl.exe i midlrt.exe, aby utworzyć pliki .h z metadanych systemu windows | Dokumentacja firmy Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4be8ba11-c223-44ad-9256-7e1edae9a7bc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 06fef7449a540fbd3cddc2d38c9ce7483a7b5d55
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2018
ms.locfileid: "33891726"
---
# <a name="how-to-use-winmdidlexe-and-midlrtexe-to-create-h-files-from-windows-metadata"></a>Porady: Użyj winmdidl.exe i midlrt.exe, aby utworzyć pliki .h z metadanych systemu Windows
Winmdidl.exe i midlrt.exe włączyć współdziałanie COM poziom natywnego kodu C++ i składników środowiska wykonawczego systemu Windows. Winmdidl.exe przyjmuje jako dane wejściowe plik winmd, który zawiera metadanych dla składnika środowiska wykonawczego systemu Windows i plik IDL. Midlrt.exe konwertuje tego pliku IDL pliki nagłówkowe, używające kod w języku C++. Zarówno narzędzia, uruchom w wierszu polecenia.  
  
 Te narzędzia można użyć w dwóch głównych scenariuszy:  
  
-   Tworzenie niestandardowych IDL i pliki nagłówkowe, aby aplikacji C++, napisane przy użyciu biblioteki szablonu środowiska wykonawczego systemu Windows (WRL), jaką może wykorzystać niestandardowych składników środowiska wykonawczego systemu Windows.  
  
-   Generowanie plików serwera proxy i klasy zastępczej dla typów zdarzeń zdefiniowanych przez użytkownika w składnika środowiska wykonawczego systemu Windows. Aby uzyskać więcej informacji, zobacz [niestandardowe zdarzenia i metod dostępu zdarzeń składników środowiska wykonawczego systemu Windows](/uwp/winrt-components/custom-events-and-event-accessors-in-windows-runtime-components).  
  
 Te narzędzia są wymagane tylko w przypadku analizy plików winmd niestandardowych. Pliki .idl i .h dla składników systemu Windows zostały już wygenerowane automatycznie. Domyślnie w [!INCLUDE[win81](../misc/includes/win81_md.md)], znajdują się one w \Program pliki (x86) \Windows Kits\8.1\Include\winrt\\.  
  
## <a name="location-of-the-tools"></a>Lokalizacja narzędzi  
 Domyślnie w [!INCLUDE[win81](../misc/includes/win81_md.md)], winmdidl.exe i midlrt.exe znajdują się w \Windows Kits\8.1 C:\Program Files (x86)\\. W folderach \bin\x86\ i \bin\x64\ również są dostępne wersje narzędzi.  
  
## <a name="winmdidl-command-line-arguments"></a>Argumenty wiersza polecenia Winmdidl  
  
```  
Winmdidl.exe [/nologo] [/supressversioncheck] [/time] [/outdir:dir] [/banner:file] [/utf8] Winmdfile  
```  
  
 `/nologo`  
 Uniemożliwia wyświetlanie konsoli winmdidl komunikat o prawach autorskich oraz numeru wersji.  
  
 `/supressversioncheck`  
 Nie używany.  
  
 `/time`  
 Wyświetla całkowity czas wykonania w danych wyjściowych konsoli.  
  
 firmy:\<dir >  
 Określa katalog danych wyjściowych. Jeśli ścieżka zawiera spacje, użyj cudzysłowów. Domyślny katalog wyjściowy jest  *\<dysku >*: \Users\\*\<nazwa użytkownika >* \AppData\Local\VirtualStore\Program pliki (x86) \Microsoft Visual Studio 12.0\\.  
  
 `/banner:<file>`  
 Określa plik, który zawiera niestandardowy tekst dołączana do domyślnego komunikat o prawach autorskich i numer wersji winmdidl u góry pliku .idl wygenerowany. Jeśli ścieżka zawiera spacje, użyj cudzysłowów.  
  
 `/utf8`  
 Powoduje, że plik jest w formacie UTF-8.  
  
 `Winmdfile`  
 Nazwa pliku winmd do analizy. Jeśli ścieżka zawiera spacje, użyj cudzysłowów.  
  
## <a name="midlrt-command-line-arguments"></a>Argumenty wiersza polecenia Midlrt  
 Zobacz [składników MIDLRT i środowiska wykonawczego systemu Windows](http://msdn.microsoft.com/library/windows/desktop/hh869900\(v=vs.85\).aspx).  
  
## <a name="examples"></a>Przykłady  
 W poniższym przykładzie przedstawiono polecenie winmdidl w wierszu polecenia programu Visual Studio x86. Określa katalog wyjściowy, a plik zawierający tekst transparentu specjalne można dodać do pliku .idl wygenerowany.  
  
 **C:\Program Files (x86) \Microsoft Visual Studio 12.0 > winmdidl/nologo /outdir:c:\users\giraffe\documents\ /banner:c:\users\giraffe\documents\banner.txt w "C:\Users\giraffe\Documents\Visual Studio 2013\Projects\Test_for_winmdidl\Debug\ Test_for_winmdidl\test_for_winmdidl.winmd"**  
  
 W kolejnym przykładzie pokazano wyświetlania konsoli z winmdidl, która wskazuje, że operacja zakończyła się pomyślnie.  
  
 **Generowanie c:\users\giraffe\documents\\\Test_for_winmdidl.idl**  
  
 Następnie midlrt jest uruchamiane w wygenerowanym pliku IDL. Zwróć uwagę, że **metadata_dir** argument zostanie określony po nazwie pliku .idl. Wymagana jest ścieżka \WinMetadata\ — jest ona lokalizacją plik windows.winmd.  
  
 **C:\Program Files (x86) \Microsoft Visual Studio 12.0 > midlrt "c:\users\mblome\documents\test_for_winmdidl.idl" /metadata_dir "C:\Windows\System32\WinMetadata"**  
  
## <a name="remarks"></a>Uwagi  
 Plik wyjściowy z operacją winmdidl ma taką samą nazwę pliku wejściowego, ale ma rozszerzenie nazwy pliku .idl.  
  
 Jeśli tworzysz składnika środowiska wykonawczego systemu Windows, w której będą mieli dostęp z biblioteki WRL, można określić winmdidl.exe i midlrt.exe do uruchamiania jako kroki mające miejsce po kompilacji, dzięki czemu plików .idl i .h są generowane dla każdej kompilacji. Na przykład zobacz [wywoływanie zdarzeń składników środowiska wykonawczego systemu Windows](/uwp/winrt-components/raising-events-in-windows-runtime-components).