---
title: Informacje w wierszu polecenia programu ML i ML64
ms.date: 08/30/2018
f1_keywords:
- ML
helpviewer_keywords:
- /W* MASM compiler option
- /c MASM compiler option
- /EP MASM compiler option
- /Fe MASM compiler option
- /Zp MASM compiler option
- /AT MASM compiler option
- /Zm MASM compiler option
- /Sf MASM compiler option
- /Sp MASM compiler option
- /w MASM compiler option
- /Fl MASM compiler option
- /coff MASM compiler option
- /St MASM compiler option
- /Cx MASM compiler option
- /Sl MASM compiler option
- /Cu MASM compiler option
- MASM (Microsoft Macro Assembler), ML command-line reference
- /FPi MASM compiler option
- /Zf MASM compiler option
- ML environment variable
- /Fr MASM compiler option
- /help MASM compiler option
- /Sa MASM compiler option
- /Zd MASM compiler option
- /I MASM compiler option
- /? MASM compiler option
- /Bl MASM compiler option
- /Fm MASM compiler option
- /Fo MASM compiler option
- command-line reference [ML]
- /Sn MASM compiler option
- /Gd MASM compiler option
- /D* MASM compiler option
- environment variables, ML
- /Gc MASM compiler option
- /F* MASM compiler option
- /Sc MASM compiler option
- /H MASM compiler option
- /Zs MASM compiler option
- /omf MASM compiler option
- /Sg MASM compiler option
- /Cp MASM compiler option
- /Zi MASM compiler option
- /nologo MASM compiler option
- /Sx MASM compiler option
- /WX MASM compiler option
- /Ss MASM compiler option
- command line, reference [ML]
- /Ta MASM compiler option
ms.assetid: 712623c6-f77e-47ea-a945-089e57c50b40
ms.openlocfilehash: a452bab03e31436ee5dde476117bce8b73c7571f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62178114"
---
# <a name="ml-and-ml64-command-line-reference"></a>Informacje w wierszu polecenia programu ML i ML64

Zbierane i łączy jeden lub więcej plików źródłowych języka asemblera. Opcje wiersza polecenia jest uwzględniana wielkość liter.

Aby uzyskać więcej informacji na temat ml64.exe, zobacz [MASM x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).

## <a name="syntax"></a>Składnia

> Uczenie Maszynowe \[ *opcje*] *filename* \[ \[ *opcje*] *filename*]
>
> ML64 \[ *opcje*] *filename* \[ \[ *opcje*] *filename*]... \[/link *linkoptions*]

### <a name="parameters"></a>Parametry

*Opcje*<br/>
Opcje wymienione w poniższej tabeli.

|Opcja|Akcja|
|------------|------------|
|**/AT**|Włącza obsługę modelu niewielki rozmiar pamięci. Umożliwia komunikaty o błędach dla konstrukcji kodu, które naruszają wymagania dotyczące plików w formacie .com. Należy pamiętać, że nie jest to równoważne [. MODEL](../../assembler/masm/dot-model.md) **bardzo MAŁA** dyrektywy.<br /><br /> Nie jest dostępna w ml64.exe.|
|**/BL** *nazwy pliku*|Wybiera alternatywne konsolidatora.|
|**/c**|Zbierane tylko. Nie łączy się.|
|**/coff**|Generuje common object format (COFF) typ pliku moduł obiektu. Ogólnie jest to wymagane dla rozwoju języka asembler Win32.<br /><br /> Nie jest dostępna w ml64.exe.|
|**/Cp**|Zachowuje wszystkie identyfikatory użytkownika wielkość liter.|
|**/Cu**|Wszystkie identyfikatory jest mapowany na wielkie litery (ustawienie domyślne).<br /><br /> Nie jest dostępna w ml64.exe.|
|**/Cx**|Zachowuje wielkość liter w symbolach publicznego i extern.|
|**/D** *symbol*[[=*wartość*]]|Definiuje makra tekstowe o podanej nazwie. Jeśli *wartość* jest Brak, jest on pusty. Wiele tokenów, rozdzielone spacjami, muszą być ujęte w znaki cudzysłowu.|
|**/EP**|Generuje listę wstępnie przetworzone źródło (wysłane do STDOUT). Zobacz **/Sf**.|
|**/ ERRORREPORT** [ **NONE** &AMP;#124; **MONITU** &AMP;#124; **KOLEJKI** &AMP;#124; **WYSYŁANIA** ]|Jeśli ml.exe lub ml64.exe zakończy się niepowodzeniem w czasie wykonywania, możesz użyć **/errorreport** do wysyłania informacji do firmy Microsoft dotyczących tych błędów wewnętrznych.<br /><br /> Aby uzyskać więcej informacji na temat **/errorreport**, zobacz [/errorreport (zgłaszaj wewnętrzne błędy kompilatora)](../../build/reference/errorreport-report-internal-compiler-errors.md).|
|**/F** *hexnum*|Ustawia rozmiar do stosu *hexnum* bajtów (to jest taka sama jak **/link/STACK**:*numer*). Wartości muszą być wyrażone w formacie szesnastkowym. Musi to być odstęp między **/F** i *hexnum*.|
|**/Fe** *nazwy pliku*|Określa nazwę pliku wykonywalnego.|
|**/FL**[[*filename*]]|Generuje listę zmontowanych kodu. Zobacz **/Sf**.|
|**/FM**[[*filename*]]|Tworzy plik mapy konsolidatora.|
|**/FO** *nazwy pliku*|Nazwy pliku obiektu. Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.|
|**/FPi**|Generuje naprawy emulator dla arytmetyki zmiennoprzecinkowej (tylko język mieszany).<br /><br /> Nie jest dostępna w ml64.exe.|
|**/FR**[[*filename*]]|Generuje plik SBR przeglądarki źródła.|
|**/FR**[[*filename*]]|Generuje rozszerzonej postaci plik SBR przeglądarki źródła.|
|**/Gc**|Określa użycie funkcji stylu FORTRAN lub Pascal wywoływania i konwencje nazewnictwa. Taki sam jak **opcji języka: PASCAL**.<br /><br /> Nie jest dostępna w ml64.exe.|
|**/Gd**|Określa użycie funkcji stylu C, wywołując i konwencje nazewnictwa. Taki sam jak **opcji języka: C**.<br /><br /> Nie jest dostępna w ml64.exe.|
|**/GZ**|Określa użycie funkcji __stdcall wywoływania i konwencje nazewnictwa.  Taki sam jak **opcji języka: STCALL**.<br /><br /> Nie jest dostępna w ml64.exe.|
|**/ H** *numer*|Ogranicza nazw zewnętrznych znaczące cyfry. Wartość domyślna to 31 znaków.<br /><br /> Nie jest dostępna w ml64.exe.|
|**/help**|Wywołuje QuickHelp, aby uzyskać pomoc dotyczącą uczenia Maszynowego.|
|**/I** *nazwy ścieżki*|Ustawia ścieżkę do pliku dołączania. Maksymalnie 10 **/I** opcje jest dozwolone.|
|**/nologo**|Pomija komunikaty dla zestawu pomyślnie.|
|**/omf**|Generuje obiekt modułu plik formatu (OMF) typ obiektu modułu.  **/ omf** oznacza **/c**; ML.exe nie obsługuje łączenie obiektów OMF.<br /><br /> Nie jest dostępna w ml64.exe.|
|**/Sa**|Włącza listę wszystkich dostępnych informacji.|
|**/safeseh**|Oznacza obiekt albo brak obsługi wyjątków lub zawierające obsługi wyjątków, zadeklarowanych przy użyciu [. SAFESEH](../../assembler/masm/dot-safeseh.md).<br /><br /> Nie jest dostępna w ml64.exe.|
|**/Sf**|Dodaje plik listy i listy pierwszego przebiegu.|
|**/SL** *szerokość*|Ustawia szerokość linii źródła w znaków w każdym wierszu. Zakres jest 60 do 255 lub 0. Domyślna to 0. Taki sam jak [strony](../../assembler/masm/page.md) szerokości.|
|**/Sn**|Wyłącza tabeli symboli podczas produkowania listę.|
|**/SP** *długość*|Ustawia długość strony źródła w wierszy na stronie. Zakres jest 10 do 255 lub 0. Domyślna to 0. Taki sam jak [strony](../../assembler/masm/page.md) długości.|
|**/Ss** *tekstu*|Określa tekst dla listy źródłowej. Taki sam jak [PODTYTUŁ](../../assembler/masm/subtitle.md) tekstu.|
|**/St** *tekstu*|Określa tytuł listy źródłowej. Taki sam jak [tytuł](../../assembler/masm/title.md) tekstu.|
|**/Sx**|Włącza false warunkowych na liście.|
|**/Ta** *nazwy pliku*|Składa plik źródłowy, którego nazwa kończy się rozszerzeniem .asm.|
|**/w**|Taki sam jak **/W0/WX**.|
|**/W** *poziom*|Ustawia poziom ostrzeżeń, gdzie *poziom* = 0, 1, 2 lub 3.|
|**/WX**|Zwraca kod błędu, jeśli zostały wygenerowane ostrzeżenia.|
|**/X**|Ignoruj ścieżkę środowiska INCLUDE.|
|**/Zd**|Generuje informacje o numerze wiersza w pliku obiektu.|
|**/Zf**|Sprawia, że wszystkie symbole publiczne.|
|**/Zi**|Generuje informacje CodeView w pliku obiektu.|
|**/Zm**|Włącza**M510** opcja maksymalny zgodności z MASM 5.1.<br /><br /> Nie jest dostępna w ml64.exe.|
|**/ ZP**[[*wyrównanie*]]|Struktury pakietów przy granic określoną liczbę bajtów. *Wyrównanie* może być 1, 2 lub 4.|
|**/Zs**|Przeprowadza tylko sprawdzanie składni.|
|**/?**|Przedstawia podsumowanie ML składni wiersza polecenia.|

*Nazwa pliku*<br/>
Nazwa pliku.

*linkoptions*<br/>
Opcje łącza.  Zobacz [opcje konsolidatora](../../build/reference/linker-options.md) Aby uzyskać więcej informacji.

## <a name="remarks"></a>Uwagi

Pewne opcje wiersza polecenia programu ML i ML64 są zależne od położenia. Na przykład ponieważ niektóre akceptuje ML i ML64 **/c** opcji i wszelkie powiązane **/Fo** opcje muszą zostać określone przed **/c**. Poniższy przykład wiersza polecenia ilustruje specyfikacji pliku obiektu, dla każdego Specyfikacja pliku zestawu:

**ml.exe /Fo a1.obj /c a.asm /Fo b1.obj /c b.asm**

## <a name="environment-variables"></a>Zmienne środowiskowe

|Zmienna|Opis|
|--------------|-----------------|
|INCLUDE|Określa ścieżkę wyszukiwania plików dołączanych.|
|ML|Określa domyślne opcje wiersza polecenia.|
|TMP|Określa ścieżkę dla plików tymczasowych.|

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)<br/>
[Microsoft Macro Assembler — dokumentacja](../../assembler/masm/microsoft-macro-assembler-reference.md)<br/>