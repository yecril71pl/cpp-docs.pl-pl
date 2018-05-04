---
title: -Gd, - Gr, - Gv, - Gz (Konwencja wywoływania) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /gr
- /Gv
- /gz
- /Gd
- VC.Project.VCCLCompilerTool.CallingConvention
dev_langs:
- C++
helpviewer_keywords:
- -Gd compiler option [C++]
- -Gv compiler option [C++]
- /Gv compiler option [C++]
- -Gr compiler option [C++]
- Gd compiler option [C++]
- Gr compiler option [C++]
- /Gz compiler option [C++]
- -Gz compiler option [C++]
- /Gd compiler option [C++]
- Gz compiler option [C++]
- Gv compiler option [C++]
- /Gr compiler option [C++]
ms.assetid: fd3110cb-2d77-49f2-99cf-a03f9ead00a3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ec0d3d7c750be9b6b6d1496c8a1e2265786264f2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="gd-gr-gv-gz-calling-convention"></a>/Gd, /Gr, /Gv, /Gz (Konwencja wywoływania)
Opcje te określają kolejność funkcji argumenty są przenoszone na stosie, czy funkcja wywołujący lub wywołana funkcja usuwa argumenty ze stosu na końcu wywołania i Konwencji dekoracji nazwa używana przez kompilator poszczególne funkcje.  
  
## <a name="syntax"></a>Składnia  
  
```  
/Gd  
/Gr  
/Gv  
/Gz  
```  
  
## <a name="remarks"></a>Uwagi  
 **/GD**, domyślne ustawienie określa [__cdecl](../../cpp/cdecl.md) Konwencję wywoływania dla wszystkich funkcji, z wyjątkiem C++ — członek, funkcji i funkcji, które są oznaczone jako [__stdcall](../../cpp/stdcall.md), [__ Fastcall](../../cpp/fastcall.md), lub [__vectorcall](../../cpp/vectorcall.md).  
  
 **GR** Określa `__fastcall` Konwencję wywoływania dla wszystkich funkcji, z wyjątkiem funkcji Członkowskich C++, funkcji o nazwie `main`i funkcje, które są oznaczone `__cdecl`, `__stdcall`, lub `__vectorcall`. Wszystkie `__fastcall` funkcje muszą mieć prototypy. Konwencja wywoływania jest dostępna tylko w kompilatorów, które odnoszą się do x86 i jest ignorowana przez kompilatorów, które odnoszą się do innych architektur.  
  
 **GZ** Określa `__stdcall` Konwencję wywoływania dla wszystkich funkcji, z wyjątkiem funkcji Członkowskich C++, funkcji o nazwie `main`i funkcje, które są oznaczone `__cdecl`, `__fastcall`, lub `__vectorcall`. Wszystkie `__stdcall` funkcje muszą mieć prototypy. Konwencja wywoływania jest dostępna tylko w kompilatorów, które odnoszą się do x86 i jest ignorowana przez kompilatorów, które odnoszą się do innych architektur.  
  
 **GV** Określa `__vectorcall` Konwencję wywoływania dla wszystkich funkcji, z wyjątkiem funkcji Członkowskich C++, funkcje głównego o nazwie, a funkcje z `vararg` listy argumentów zmiennych lub funkcje, które są oznaczone ikoną z powodujące konflikt `__cdecl`, `__stdcall`, lub `__fastcall` atrybutu. Konwencja wywoływania jest dostępna tylko w x86 i x64 architektury, które obsługują SSE2 lub nowszym i jest ignorowana przez kompilatorów, które odnoszą się do architektury ARM.  
  
 Funkcje, których zmienna liczba argumentów muszą być oznaczone jako `__cdecl`.  
  
 **/GD**, **GR**, **GV** i **GZ** nie są zgodne z [/CLR: Safe](../../build/reference/clr-common-language-runtime-compilation.md) lub   **/CLR: pure**. **/CLR: pure** i **/CLR: Safe** — opcje kompilatora zostały uznane za przestarzałe w programie Visual Studio 2015.  
  
> [!NOTE]
>  Domyślnie dla x86 procesorów, funkcji Członkowskich C++ użyj [__thiscall](../../cpp/thiscall.md).  
  
 Dla wszystkich procesorów, funkcji członkowskiej, która jest wyraźnie oznaczona jako `__cdecl`, `__fastcall`, `__vectorcall`, lub `__stdcall` używa konwencji wywoływania określona, jeśli nie jest ignorowana w danej architekturze. Funkcja elementu członkowskiego, który przyjmuje zmienną liczbę argumentów zawsze używa `__cdecl` konwencji wywoływania.  
  
 Te opcje kompilatora nie mają wpływu na nazwij dekorację metody C++ i funkcji. O ile nie jest zadeklarowany jako `extern "C"`, metody C++ i funkcji używanie różnych dekoracji nazwy schematu. Aby uzyskać więcej informacji, zobacz [dekorowane nazwy](../../build/reference/decorated-names.md).  
  
 Aby uzyskać więcej informacji na temat konwencji wywoływania, zobacz [konwencji wywoływania](../../cpp/calling-conventions.md).  
  
## <a name="cdecl-specifics"></a>Szczegóły __cdecl  
 Na x86 procesorów, wszystkie argumenty funkcji są przekazywane na stosie od prawej do lewej. Na ARM i x64 architektury, niektóre argumenty są przekazywane przez rejestr, a pozostałe są przekazywane na stosie od prawej do lewej. Wywołanie procedury POP argumentów ze stosu.  
  
 Dla języka C `__cdecl` nazewnictwa używa konwencji nazwą funkcji poprzedzone znaku podkreślenia ( `_` ); odbywa się bez przypadków translacji. O ile nie jest zadeklarowany jako `extern "C"`, funkcje języka C++ Użyj innego schematu dekoracji nazwy. Aby uzyskać więcej informacji, zobacz [dekorowane nazwy](../../build/reference/decorated-names.md).  
  
## <a name="fastcall-specifics"></a>Szczegóły __fastcall  
 Niektóre `__fastcall` argumenty funkcji są przekazywane w rejestrach (dla x86 procesory, ECX i EDX), a pozostałe są przenoszone na stosie od prawej do lewej. Wywołana procedura POP tych argumentów ze stosu przed zwróceniem. Zazwyczaj **GR** skraca czas wykonywania.  
  
> [!NOTE]
>  Należy zachować ostrożność, korzystając z `__fastcall` Konwencję wywoływania dla dowolnej funkcji, jest napisany w języku zestawu wbudowanego. Korzystanie z rejestrów może powodować konflikt z użyciem kompilatora.  
  
 Dla języka C `__fastcall` nazewnictwa używa konwencji nazwą funkcji poprzedzone znakiem (`@`) następuje rozmiar argumentów funkcji w bajtach. Odbywa się bez przypadków translacji. Kompilator używa tego szablonu do konwencji nazewnictwa:  
  
```  
@function_name@number  
```  
  
 Jeśli używasz `__fastcall` konwencji nazewnictwa, użyj plików dołączanych standardowa. W przeciwnym razie wystąpi nierozpoznanych odwołań zewnętrznych.  
  
## <a name="stdcall-specifics"></a>Szczegóły __stdcall  
 A `__stdcall` argumenty funkcji są przenoszone na stosie od prawej do lewej, a następnie wywołana funkcja POP tych argumentów ze stosu przed zwróceniem.  
  
 Dla języka C `__stdcall` nazewnictwa używa konwencji nazwą funkcji poprzedzone znaku podkreślenia ( `_` ) i następuje znak (@), a rozmiar argumentów funkcji w bajtach. Nie przypadków tłumaczenia jest wykonywane. Kompilator używa tego szablonu do konwencji nazewnictwa:  
  
```  
_functionname@number  
```  
  
## <a name="vectorcall-specifics"></a>Szczegóły __vectorcall  
 A `__vectorcall` funkcji całkowitą argumenty są przekazywane przez wartość, przy użyciu maksymalnie dwa (na x86) lub cztery (na x64) całkowitą rejestruje i maksymalnie sześć XMM rejestruje zmiennoprzecinkowych i wektor wartości, a pozostałe są przekazywane na stosie od prawej do lewej. Wywoływana funkcja czyści ze stosu przed zwróceniem. Wektor i zmiennoprzecinkowych wartości zwracane są zwracane w XMM0.  
  
 Dla języka C `__vectorcall` konwencji nazewnictwa używa nazwę funkcji, a następnie dwoma znakami (@@) oraz rozmiar argumentów funkcji w bajtach. Nie przypadków tłumaczenia jest wykonywane. Kompilator używa tego szablonu do konwencji nazewnictwa:  
  
```  
functionname@@number  
```  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **strony właściwości** okno dialogowe. Aby uzyskać więcej informacji, zobacz [Praca z właściwościami projektu](../../ide/working-with-project-properties.md).  
  
2.  Wybierz **C/C++** folderu.  
  
3.  Wybierz **zaawansowane** strony właściwości.  
  
4.  Modyfikowanie **konwencji wywoływania** właściwości.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Aby programowo ustawić tę opcję kompilatora  
  
-   Zobacz <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CallingConvention%2A>.  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora](../../build/reference/compiler-options.md)   
 [Ustawianie opcji kompilatora](../../build/reference/setting-compiler-options.md)