---
title: 'Instrukcje: Użyj winmdidl.exe i midlrt.exe, aby utworzyć pliki .h z metadanych systemu windows'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 4be8ba11-c223-44ad-9256-7e1edae9a7bc
ms.openlocfilehash: b9016f05b82e3eb04474d370bd069e8008de5278
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58787280"
---
# <a name="how-to-use-winmdidlexe-and-midlrtexe-to-create-h-files-from-windows-metadata"></a>Instrukcje: Użyj winmdidl.exe i midlrt.exe, aby utworzyć pliki .h z metadanych systemu windows

Winmdidl.exe i midlrt.exe włączyć współdziałanie COM poziom macierzystego kodu C++ i składników środowiska wykonawczego Windows. Winmdidl.exe przyjmuje jako dane wejściowe plik .winmd, który zawiera metadane dla składnika wykonawczego Windows, a następnie generuje pliku IDL. Midlrt.exe konwertuje ten plik IDL pliki nagłówkowe, używające kodu C++. Oba narzędzia Uruchom w wierszu polecenia.

Można użyć tych narzędzi w dwa główne scenariusze:

- Tworzenie niestandardowych IDL i pliki nagłówkowe, tak, aby napisane przy użyciu biblioteki szablonów środowiska uruchomieniowego Windows (WRL) aplikacji w języku C++ mogą wykorzystywać niestandardowych składników Windows Runtime.

- Generowanie plików serwera proxy i klas zastępczych dla typów zdarzeń zdefiniowanych przez użytkownika w składnika środowiska wykonawczego Windows. Aby uzyskać więcej informacji, zobacz [niestandardowe zdarzenia i metody dostępu zdarzeń w składnikach środowiska wykonawczego Windows](/windows/uwp/winrt-components/custom-events-and-event-accessors-in-windows-runtime-components).

Te narzędzia są wymagane tylko w przypadku analizowania plików winmd niestandardowych. Plików .idl i .h składników systemu operacyjnego Windows już są generowane dla Ciebie. Domyślnie w Windows 8.1 znajdują się one w \Program pliki (x86) \Windows Kits\8.1\Include\winrt\\.

## <a name="location-of-the-tools"></a>Lokalizacja narzędzi

Domyślnie w [Windows 8.1, winmdidl.exe i midlrt.exe, które znajdują się w \Windows Kits\8.1 C:\Program Files (x86)\\. Wersja narzędzia są dostępne również w folderach \bin\x86\ i \bin\x64\.

## <a name="winmdidl-command-line-arguments"></a>Argumenty wiersza polecenia Winmdidl

```
Winmdidl.exe [/nologo] [/suppressversioncheck] [/time] [/outdir:dir] [/banner:file] [/utf8] Winmdfile
```

**/nologo**<br/>
Uniemożliwia wyświetlanie konsoli winmdidl komunikat o prawach autorskich oraz numeru wersji.

**/suppressversioncheck**<br/>
Nie używany.

**/ Godzina**<br/>
Przedstawia całkowity czas wykonywania w danych wyjściowych konsoli.

**do pliku klucza:**<em>dir</em><br/>
Określa katalog danych wyjściowych. Jeśli ścieżka zawiera spacje, użyj znaków cudzysłowu. Domyślny katalog danych wyjściowych jest  *\<dysku >*: \Users\\*\<username >* \AppData\Local\VirtualStore\Program Files (x86) \Microsoft Visual Studio 12.0\\.

**/ Baner:**<em>pliku</em><br/>
Określa plik, który zawiera niestandardowy tekst być dołączana do domyślny komunikat o prawach autorskich oraz winmdidl numer wersji w górnej części pliku .idl wygenerowany. Jeśli ścieżka zawiera spacje, użyj znaków cudzysłowu.

**/UTF8**<br/>
Powoduje, że plik aby być w formacie UTF-8.

*Winmdfile*<br/>
Nazwa pliku winmd, które można przeanalizować. Jeśli ścieżka zawiera spacje, użyj znaków cudzysłowu.

## <a name="midlrt-command-line-arguments"></a>Argumenty wiersza polecenia Midlrt

Zobacz [MIDLRT i środowiska wykonawczego Windows składników](/windows/desktop/Midl/midlrt-and-windows-runtime-components).

## <a name="examples"></a>Przykłady

Poniższy przykład pokazuje winmdidl polecenie w wierszu polecenia programu Visual Studio x86. Określa katalog wyjściowy, a plik, który zawiera tekst transparentu specjalne do dodania do pliku .idl wygenerowany.

`C:\Program Files (x86)\Microsoft Visual Studio 12.0>winmdidl /nologo /outdir:c:\users\giraffe\documents\ /banner:c:\users\giraffe\documents\banner.txt "C:\Users\giraffe\Documents\Visual Studio 2013\Projects\Test_for_winmdidl\Debug\Test_for_winmdidl\test_for_winmdidl.winmd"`

W kolejnym przykładzie pokazano wyświetlania konsoli z winmdidl, która wskazuje, że operacja zakończyła się pomyślnie.

**Generating c:\users\giraffe\documents\\\Test_for_winmdidl.idl**

Następnie midlrt jest uruchamiane w wygenerowanym pliku IDL. Należy zauważyć, że **metadata_dir** argument zostanie określony po nazwie pliku .idl. Wymagana jest ścieżka \WinMetadata\ — jest ona lokalizacją windows.winmd.

`C:\Program Files (x86)\Microsoft Visual Studio 12.0> midlrt "c:\users\mblome\documents\test_for_winmdidl.idl" /metadata_dir "C:\Windows\System32\WinMetadata"`

## <a name="remarks"></a>Uwagi

Plik wyjściowy z operacją winmdidl ma taką samą nazwę jak plik wejściowy, ale ma rozszerzenie nazwy pliku .idl.

Jeśli tworzysz składnik środowiska wykonawczego Windows, który uzyskuje się dostęp z WRL można określić winmdidl.exe i midlrt.exe, aby uruchomić jako kroków wykonywanych po kompilacji, tak, aby plików .idl i .h są generowane dla każdej kompilacji. Aby uzyskać przykład, zobacz [Raising Events w składnikach środowiska wykonawczego Windows](/windows/uwp/winrt-components/raising-events-in-windows-runtime-components).