---
title: Informacje w wierszu polecenia programu ML i ML64
ms.date: 12/17/2019
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
ms.openlocfilehash: 77385317ab7f90a646b7f552e471d0f434e72bfb
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317165"
---
# <a name="ml-and-ml64-command-line-reference"></a>Informacje w wierszu polecenia programu ML i ML64

Tworzy i łączy jeden lub więcej plików źródłowych języka asemblera. W opcjach wiersza polecenia jest rozróżniana wielkość liter.

Aby uzyskać więcej informacji na temat ml64. exe, zobacz [MASM for x64 (ml64. exe)](masm-for-x64-ml64-exe.md).

## <a name="syntax"></a>Składnia

> ML \[*Opcje*] *filename* \[ \[*Opcje*] *Nazwa pliku*]
>
> ML64 \[*Opcje*] *filename* \[ \[*Opcje*] *Nazwa pliku*]... \[/link *linkOptions*]

### <a name="parameters"></a>Parametry

*opcje*\
Opcje wymienione w poniższej tabeli.

|Opcja|Akcja|
|------------|------------|
|**/AT**|Włącza obsługę modelu z niewielką ilością pamięci. Włącza komunikaty o błędach dla konstrukcji kodu, które naruszają wymagania dotyczące plików w formacie. com. Należy zauważyć, że nie jest to odpowiednik [. ](dot-model.md) **Niewielka** dyrektywa modelu.<br /><br /> Niedostępne w ml64. exe.|
|*Nazwa pliku* /BL|Wybiera alternatywny konsolidator.|
|**/c**|Tylko składowe. Nie łączy.|
|**/coff**|Generuje typ modułu obiektów Common File Format (COFF). Zwykle wymagane do tworzenia języka zestawu Win32.<br /><br /> Niedostępne w ml64. exe.|
|**/CP**|Zachowuje wielkość liter wszystkich identyfikatorów użytkowników.|
|**/Cu**|Mapuje wszystkie identyfikatory na wielkie litery (domyślnie).<br /><br /> Niedostępne w ml64. exe.|
|**/Cx**|Zachowuje wielkość liter w publicznych i zewnętrznych symbolach.|
|**/D** *symbol*⟦ =*Value*⟧|Definiuje makro tekstowe o podaną nazwę. Jeśli brakuje *wartości* , jest ona pusta. Wiele tokenów rozdzielonych spacjami musi być ujęte w cudzysłów.|
|**/EP**|Generuje listę wstępnie przetworzonych źródeł (wysyłanych do STDOUT). Zobacz **/SF**.|
|**/errorreport** [ **Brak** &#124; **monitu o potwierdzenie** &#124; **kolejki** &#124; **]**|Jeśli program ml. exe lub ml64. exe kończy się niepowodzeniem w czasie wykonywania, można użyć **/errorreport** do wysłania informacji o tych błędach wewnętrznych do firmy Microsoft.<br /><br /> Aby uzyskać więcej informacji na temat **/errorreport**, zobacz [/errorreport (zgłaszaj wewnętrzne błędy kompilatora)](../../build/reference/errorreport-report-internal-compiler-errors.md).|
|**/F** *hexnum*|Ustawia rozmiar stosu na *hexnum* bajtów (jest to taka sama jak **/link/Stack**:*Number*). Wartość musi być wyrażona w notacji szesnastkowej. Między **/f** i *hexnum*musi znajdować się spacja.|
|*Nazwa pliku* /Fe|Nazwa pliku wykonywalnego.|
|**/FL**⟦*filename*⟧|Generuje listę zebranych kodu. Zobacz **/SF**.|
|**/FM**⟦*filename*⟧|Tworzy plik mapy konsolidatora.|
|**/Fo** *filename*|Nazwa pliku obiektu. Aby uzyskać więcej informacji, zobacz sekcję Uwagi.|
|**/FPi**|Generuje rozwiązanie emulatora dla operacji arytmetycznych zmiennoprzecinkowych (tylko w języku mieszanym).<br /><br /> Niedostępne w ml64. exe.|
|**/Fr**⟦*filename*⟧|Generuje plik źródłowy przeglądarki. sbr.|
|**/Fr**⟦*filename*⟧|Generuje rozszerzoną postać pliku źródłowego Browser. sbr.|
|**/Gc**|Określa użycie funkcji w stylu języka Pascala Pascal lub konwencji nazewnictwa. Analogicznie jak **Język opcji: Pascal**.<br /><br /> Niedostępne w ml64. exe.|
|**/Gd**|Określa użycie funkcji w stylu języka C i konwencji nazewnictwa. Analogicznie jak **Język opcji: C**.<br /><br /> Niedostępne w ml64. exe.|
|**/GZ**|Określa użycie funkcji __stdcall wywoływania i konwencji nazewnictwa.  Analogicznie jak **Język opcji: STCALL**.<br /><br /> Niedostępne w ml64. exe.|
|*Numer* /h|Ogranicza nazwy zewnętrzne do liczby znaków znaczących. Wartość domyślna to 31 znaków.<br /><br /> Niedostępne w ml64. exe.|
|**/help**|Wywołuje QuickHelp w celu uzyskania pomocy dotyczącej ML.|
|**/I** *Nazwa ścieżki*|Ustawia ścieżkę dla pliku dołączanego. Dozwolone są **maksymalnie 10 opcji** .|
|**/nologo**|Pomija komunikaty dla pomyślnego zestawu.|
|**/omf**|Generuje typ modułu obiektu w formacie pliku modułu obiektów (OMF).  **/OMF** oznacza **/c**; Program ML. exe nie obsługuje łączenia obiektów OMF.<br /><br /> Niedostępne w ml64. exe.|
|**/Sa**|Włącza listę wszystkich dostępnych informacji.|
|**/SAFESEH**|Oznacza obiekt jako zawierający brak obsługi wyjątków lub zawierający programy obsługi wyjątków, które są zadeklarowane z [. SAFESEH](dot-safeseh.md).<br /><br /> Niedostępne w ml64. exe.|
|**/Sf**|Dodaje listę pierwszego przebiegu, aby wyświetlić listę plików.|
|*Szerokość* /SL|Ustawia szerokość linii listy źródłowej w znakach na wiersz. Zakresem jest 60 do 255 lub 0. Wartość domyślna to 0. Taka sama jak szerokość [strony](page.md) .|
|**/Sn**|Wyłącza tabelę symboli podczas tworzenia listy.|
|*Długość* /Sp|Ustawia długość strony listy źródłowej w wierszach na stronę. Zakresem jest 10 do 255 lub 0. Wartość domyślna to 0. Taka sama jak długość [strony](page.md) .|
|**/SS** *tekst*|Określa tekst dla listy źródłowej. Taki sam jak tekst [podtytułu](subtitle.md) .|
|*Tekst* /St|Określa tytuł dla listy źródłowej. Taki sam jak tekst [tytułu](title.md) .|
|**/Sx**|Włącza na liście wartość false.|
|*Nazwa pliku* /ta|Składa plik źródłowy, którego nazwa nie kończy się rozszerzeniem. asm.|
|**/w**|Analogicznie jak **/W0/WX**.|
|**/W** — *poziom*|Ustawia poziom ostrzeżeń, gdzie *Level* = 0, 1, 2 lub 3.|
|**/WX**|Zwraca kod błędu, jeśli są generowane ostrzeżenia.|
|**/X**|Ignoruj ścieżkę środowiska INCLUDE.|
|**/Zd**|Generuje informacje o liczbie wierszy w pliku obiektu.|
|**/Zf**|Sprawia, że wszystkie symbole są publiczne.|
|**/Zi**|Generuje informacje CodeView w pliku obiektu.|
|**/Zm**|Włącza opcję**M510** dla maksymalnej zgodności z MASM 5,1.<br /><br /> Niedostępne w ml64. exe.|
|**/ZP**⟦*wyrównania*⟧|Struktury pakietów na określonej granicy bajtów. *Wyrównanie* może mieć wartość 1, 2 lub 4.|
|**/Zs**|Wykonuje tylko sprawdzanie składni.|
|**/?**|Wyświetla podsumowanie składni wiersza polecenia ML.|

*Nazwa pliku*\
Nazwa pliku.

*linkoptions*\
Opcje łącza.  Aby uzyskać więcej informacji, zobacz [Opcje konsolidatora](../../build/reference/linker-options.md) .

## <a name="remarks"></a>Uwagi

Niektóre opcje wiersza polecenia do ML i ML64 są zależne od położenia. Na przykład, ponieważ ML i ML64 mogą akceptować kilka **/c** opcji, wszystkie odpowiednie opcje **/fo** muszą zostać określone przed **/c**. Poniższy przykład wiersza polecenia ilustruje specyfikację pliku obiektu dla każdej specyfikacji pliku zestawu:

**ml.exe /Fo a1.obj /c a.asm /Fo b1.obj /c b.asm**

## <a name="environment-variables"></a>Zmienne środowiskowe

|Zmienna|Opis|
|--------------|-----------------|
|INCLUDE|Określa ścieżkę wyszukiwania dla plików dołączanych.|
|ML|Określa domyślne opcje wiersza polecenia.|
|TMP|Określa ścieżkę dla plików tymczasowych.|

## <a name="see-also"></a>Zobacz także

[Komunikaty o błędach ML](ml-error-messages.md)\
[Microsoft Macro Assembler — dokumentacja](microsoft-macro-assembler-reference.md)
