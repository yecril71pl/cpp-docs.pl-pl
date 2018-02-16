---
title: Informacje w wierszu polecenia programu ML i ML64 | Dokumentacja firmy Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ML
dev_langs:
- C++
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
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: edb7f0c19e9517b1bcefcc2400542f910a73c8f0
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2018
---
# <a name="ml-and-ml64-command-line-reference"></a>Informacje w wierszu polecenia programu ML i ML64
Składana i łączy co najmniej jeden plik źródłowy języka zestawu. Opcje wiersza polecenia jest uwzględniana wielkość liter.  
  
 Aby uzyskać więcej informacji o ml64.exe, zobacz [MASM dla x64 (ml64.exe)](../../assembler/masm/masm-for-x64-ml64-exe.md).  
  
## <a name="syntax"></a>Składnia  
  
```  
ML [[options]] filename [[ [[options]]  filename]]  
ML64 [[options]] filename [[ [[options]]  filename]]  
...  
[[/link linkoptions]]  
```  
  
#### <a name="parameters"></a>Parametry  
 `options`  
 Opcje wymienione w poniższej tabeli.  
  
|Opcja|Akcja|  
|------------|------------|  
|**/AT**|Włącza obsługę modelu niewielki rozmiar pamięci. Umożliwia komunikaty o błędach dla konstrukcji kodu, które narusza wymagania dotyczące plików w formacie .com. Należy pamiętać, że nie jest odpowiednikiem [. MODEL](../../assembler/masm/dot-model.md) **bardzo MAŁA** dyrektywy.<br /><br /> Nie jest dostępna w ml64.exe.|  
|**/BL** `filename`|Wybiera alternatywny konsolidatora.|  
|**/c**|Składana tylko. Nie zawiera łączy.|  
|**/coff**|Generuje wspólne typ formatu (COFF) pliku obiektu obiektu modułu. Zwykle wymagane przez programowanie języka zestawu Win32.<br /><br /> Nie jest dostępna w ml64.exe.|  
|**/CP**|Zachowuje przypadku wszystkie identyfikatory użytkowników.|  
|**/Cu**|Wszystkie identyfikatory jest mapowany na wielkie litery (ustawienie domyślne).<br /><br /> Nie jest dostępna w ml64.exe.|  
|**/Cx**|Zachowuje wielkość liter w publicznym i extern symboli.|  
|**/D** `symbol`[[=`value`]]|Określa tekst makra o podanej nazwie. Jeśli `value` jest Brak, jest pusta. Wiele tokenów rozdzielone spacjami musi być ujęta w cudzysłów.|  
|**/EP**|Generuje listę wstępnie przetworzonych źródła (wysyłane do STDOUT). Zobacz **/Sf**.|  
|**/ ERRORREPORT** [ **BRAK** &#124; **MONITU** &#124; **KOLEJKI** &#124; **WYSYŁANIA** ]|Jeśli ml.exe lub ml64.exe kończy się niepowodzeniem w czasie wykonywania, możesz użyć **/errorreport** wysyłać informacje do firmy Microsoft informacji o tych błędach wewnętrznych.<br /><br /> Aby uzyskać więcej informacji na temat **/errorreport**, zobacz [/errorreport (zgłaszaj wewnętrzne błędy kompilatora)](../../build/reference/errorreport-report-internal-compiler-errors.md).|  
|**/F** `hexnum`|Ustawia rozmiar do stosu `hexnum` bajtów (to jest taka sama jak **/link/STOS**:`number`). Wartość musi być wyrażony w formacie szesnastkowym. Musi istnieć odstęp między **/F** i `hexnum`.|  
|**/Fe** `filename`|Określa nazwę pliku wykonywalnego.|  
|**/Fl**[[`filename`]]|Generuje listę złożony kodu. Zobacz **/Sf**.|  
|**/Fm**[[`filename`]]|Tworzy plik mapy konsolidatora.|  
|**/FO** `filename`|Nazwy pliku obiektu. Więcej informacji podano w sekcji uwag.|  
|**/FPi**|Generuje naprawy emulatora dla liczb zmiennoprzecinkowych arytmetyczne (tylko język mieszane).<br /><br /> Nie jest dostępna w ml64.exe.|  
|**/FR**[[`filename`]]|Generuje plik .sbr przeglądarki źródła.|  
|**/FR**[[`filename`]]|Generuje rozszerzonej formy plik .sbr przeglądarki źródła.|  
|**/Gc**|Określa użycie funkcji styl FORTRAN lub Pascal wywoływania i konwencje nazewnictwa. Taki sam jak **opcji języka: PASCAL**.<br /><br /> Nie jest dostępna w ml64.exe.|  
|**/Gd**|Określa użycie funkcji stylu języka C wywoływania i konwencje nazewnictwa. Taki sam jak **opcji języka: C**.<br /><br /> Nie jest dostępna w ml64.exe.|  
|**/GZ**|Określa użycie funkcji __stdcall wywoływania i konwencje nazewnictwa.  Taki sam jak **opcji języka: STCALL**.<br /><br /> Nie jest dostępna w ml64.exe.|  
|**/H** `number`|Ogranicza nazw zewnętrznych numerów znaki znaczące. Wartość domyślna to 31 znaków.<br /><br /> Nie jest dostępna w ml64.exe.|  
|**/help**|Wywołuje QuickHelp, aby uzyskać pomoc dotyczącą uczenia Maszynowego.|  
|**/I** `pathname`|Ustawia ścieżkę do pliku include. Maksymalnie 10 **/I** opcje jest dozwolone.|  
|**/nologo**|Pomija wiadomości dla zestawu powiodło się.|  
|**/omf**|Generuje typ obiektu modułu pliku formatu (OMF) obiektu modułu.  **/ omf** oznacza **/c**; ML.exe nie obsługuje tworzenia połączeń obiektów OMF.<br /><br /> Nie jest dostępna w ml64.exe.|  
|**/Sa**|Włącza listę wszystkich dostępnych informacji.|  
|**/safeseh**|Oznacza obiekt jako albo niezawierające nie programów obsługi wyjątków lub zawierające programy obsługi wyjątków, zadeklarowane za [. SAFESEH](../../assembler/masm/dot-safeseh.md).<br /><br /> Nie jest dostępna w ml64.exe.|  
|**/Sf**|Dodaje Przekaż pierwszy plik listy do listy.|  
|**/Sl** `width`|Ustawia szerokość linii źródła w znaków w wierszu. Zakres to 60 do 255 lub 0. Domyślna to 0. Taki sam jak [strony](../../assembler/masm/page.md) szerokości.|  
|**/Sn**|Wyłącza tabeli symboli podczas produkowania na liście.|  
|**/SP** `length`|Ustawia długość strony źródła w wierszy na stronie. Zakres jest 10 do 255 lub 0. Domyślna to 0. Taki sam jak [strony](../../assembler/masm/page.md) długości.|  
|**/Ss** `text`|Określa tekst dla listy źródłowej. Taki sam jak [PODTYTUŁ](../../assembler/masm/subtitle.md) tekstu.|  
|**/St** `text`|Określa tytuł listy źródłowej. Taki sam jak [tytuł](../../assembler/masm/title.md) tekstu.|  
|**/Sx**|Włącza false warunków na liście.|  
|**/Ta** `filename`|Składana plik źródłowy, której nazwa kończy się rozszerzeniem .asm.|  
|**/w**|Taki sam jak **/W0/WX**.|  
|**/W** `level`|Ustawia poziom ostrzeżeń, gdzie `level` = 0, 1, 2 lub 3.|  
|**/WX**|Zwraca kod błędu, jeśli ostrzeżenia zostały wygenerowane.|  
|**/X**|Ignoruj ścieżkę do ZAŁĄCZENIA środowiska.|  
|**/Zd**|Generuje informacje o numerze wiersza w pliku obiektu.|  
|**/Zf**|Powoduje, że wszystkie symbole publiczne.|  
|**/Zi**|Generuje informacje CodeView w pliku obiektu.|  
|**/Zm**|Umożliwia**M510** opcję maksymalną zgodność z MASM 5.1.<br /><br /> Nie jest dostępna w ml64.exe.|  
|**/Zp**[[`alignment`]]|Struktury pakietów przy określonym bajcie granic. `alignment` Może być 1, 2 lub 4.|  
|**/Zs**|Przeprowadza tylko sprawdzanie składni.|  
|**/?**|Wyświetla podsumowanie ML składni wiersza polecenia.|  
  
 `filename`  
 Nazwa pliku.  
  
 `linkoptions`  
 Opcje link.  Zobacz [opcje konsolidatora](../../build/reference/linker-options.md) Aby uzyskać więcej informacji.  
  
## <a name="remarks"></a>Uwagi  
 Niektóre opcje wiersza polecenia programu ML i ML64 są zależne od umieszczania. Na przykład ponieważ kilka akceptuje ML i ML64 **/c** opcje żadnych odpowiadającego **/Fo** opcje muszą zostać określone przed **/c**. Poniższy przykład wiersza polecenia przedstawia specyfikacji pliku obiektu dla każdego Specyfikacja pliku zestawu:  
  
 **ml.exe /Fo a1.obj /c a.asm /Fo b1.obj /c b.asm**  
  
## <a name="environment-variables"></a>Zmienne środowiskowe  
  
|Zmienna|Opis|  
|--------------|-----------------|  
|INCLUDE|Określa ścieżkę wyszukiwania plików dołączanych.|  
|ML|Określa domyślne opcje wiersza polecenia.|  
|TMP|Określa ścieżkę do plików tymczasowych.|  
  
## <a name="see-also"></a>Zobacz też  
 [Komunikaty o błędach ML](../../assembler/masm/ml-error-messages.md)   
 [Microsoft Macro Assembler — dokumentacja](../../assembler/masm/microsoft-macro-assembler-reference.md)