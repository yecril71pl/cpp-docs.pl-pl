---
title: Wywoływanie funkcji natywnych z kodu zarządzanego
ms.date: 11/04/2016
helpviewer_keywords:
- native functions called from managed code [C++]
- managed code [C++], interoperability
- platform invoke [C++], interoperability
- interoperabiliy [C++], calling native functions from managed code
- calling native functions from managed code
- interop [C++], calling native functions from managed code
ms.assetid: 982cef18-20d9-42b4-8242-a77fa65f2e36
ms.openlocfilehash: 0cdd5db4fae8d9167fa9ab1aeb6a4e8cbfe76ded
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372511"
---
# <a name="calling-native-functions-from-managed-code"></a>Wywoływanie funkcji natywnych z kodu zarządzanego

Środowisko wykonawcze języka wspólnego zapewnia usługi wywołania platformy lub PInvoke, który umożliwia kod zarządzany do wywoływania funkcji w stylu C w natywnych bibliotek połączonych dynamicznie (DLL). Ten sam organizowanie danych jest używany jako interoperacyjność COM z środowiska wykonawczego i "To po prostu działa" lub IJW, mechanizm.

Aby uzyskać więcej informacji, zobacz:

- [Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

- [Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

Przykłady w tej sekcji tylko `PInvoke` ilustrują, jak można użyć. `PInvoke`można uprościć niestandardowe organizowanie danych, ponieważ udostępniasz informacje deklaratywnie w atrybutach zamiast pisania kodu organizowania proceduralnego.

> [!NOTE]
> Biblioteka organizowania udostępnia alternatywny sposób organizowania danych między środowiskami macierzystymi i zarządzanymi w sposób zoptymalizowany. Zobacz [omówienie organizowania w języku C++,](../dotnet/overview-of-marshaling-in-cpp.md) aby uzyskać więcej informacji na temat biblioteki organizowania. Biblioteka organizowania jest dostępna tylko dla danych, a nie dla funkcji.

## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke i atrybut DllImport

Poniższy przykład przedstawia `PInvoke` użycie w programie Visual C++. Funkcja macierzysta stawia jest zdefiniowana w pliku msvcrt.dll. Atrybut DllImport jest używany dla deklaracji stawia.

```cpp
// platform_invocation_services.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[DllImport("msvcrt", CharSet=CharSet::Ansi)]
extern "C" int puts(String ^);

int main() {
   String ^ pStr = "Hello World!";
   puts(pStr);
}
```

Poniższa próbka jest równoważna poprzedniej próbce, ale używa IJW.

```cpp
// platform_invocation_services_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

#include <stdio.h>

int main() {
   String ^ pStr = "Hello World!";
   char* pChars = (char*)Marshal::StringToHGlobalAnsi(pStr).ToPointer();
   puts(pChars);

   Marshal::FreeHGlobal((IntPtr)pChars);
}
```

### <a name="advantages-of-ijw"></a>Zalety IJW

- Nie ma potrzeby `DLLImport` pisania deklaracji atrybutów dla niezarządzanych interfejsów API używanych przez program. Wystarczy dołączyć plik nagłówka i połączyć się z biblioteką importu.

- Mechanizm IJW jest nieco szybszy (na przykład wycinki IJW nie trzeba sprawdzać, czy nie trzeba przypinać lub kopiować elementów danych, ponieważ jest to wykonywane jawnie przez dewelopera).

- Wyraźnie ilustruje problemy z wydajnością. W takim przypadku fakt, że są tłumaczenia z ciągu Unicode do ciągu ANSI i że masz towarzyszących alokacji pamięci i dezlokacji. W takim przypadku deweloper piszący kod przy użyciu `_putws` IJW zda sobie sprawę, że wywołanie i używanie `PtrToStringChars` byłoby lepsze pod względem wydajności.

- Jeśli wywołasz wiele niezarządzanych interfejsów API przy użyciu tych samych danych, kierowanie go raz i przekazywanie marshaled kopii jest znacznie bardziej wydajne niż ponowne kierowanie za każdym razem.

### <a name="disadvantages-of-ijw"></a>Wady IJW

- Kierowanie musi być wyraźnie określone w kodzie, a nie przez atrybuty (które często mają odpowiednie ustawienia domyślne).

- Kod kierowanie jest wbudowany, gdzie jest bardziej inwazyjne w przepływie logiki aplikacji.

- Ponieważ jawne kierowanie interfejsów API zwraca `IntPtr` typy dla 32-bitowej do `ToPointer` 64-bitowej przenośności, należy użyć dodatkowych wywołań.

Specyficzna metoda widoczna przez C++ jest bardziej wydajną, jawną metodą, kosztem pewnej dodatkowej złożoności.

Jeśli aplikacja używa głównie niezarządzanych typów danych lub jeśli wywołuje więcej niezarządzanych interfejsów API niż interfejsy API programu .NET Framework, zaleca się użycie funkcji IJW. Aby wywołać okazjonalne niezarządzanego interfejsu API w aplikacji głównie zarządzane, wybór jest bardziej subtelne.

## <a name="pinvoke-with-windows-apis"></a>PInvoke z interfejsami API systemu Windows

PInvoke jest wygodny do wywoływania funkcji w systemie Windows.

W tym przykładzie program Visual C++ współpracuje z funkcją MessageBox, która jest częścią interfejsu API Systemu Win32.

```cpp
// platform_invocation_services_4.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;
typedef void* HWND;
[DllImport("user32", CharSet=CharSet::Ansi)]
extern "C" int MessageBox(HWND hWnd, String ^ pText, String ^ pCaption, unsigned int uType);

int main() {
   String ^ pText = "Hello World! ";
   String ^ pCaption = "PInvoke Test";
   MessageBox(0, pText, pCaption, 0);
}
```

Dane wyjściowe to okno komunikatu, które ma tytuł PInvoke Test i zawiera tekst Hello World!.

Informacje o kierowaniu są również używane przez PInvoke do wyszukiwania funkcji w biblioteki DLL. W user32.dll w rzeczywistości nie ma funkcji MessageBox, ale CharSet=CharSet::Ansi umożliwia PInvoke korzystanie z MessageBoxA, wersji ANSI, zamiast MessageBoxW, która jest wersją Unicode. Ogólnie rzecz biorąc zaleca się używanie wersji Unicode niezarządzanych interfejsów API, ponieważ eliminuje to obciążenie związane z tłumaczeniem z macierzystego formatu Unicode obiektów ciągów .NET Framework do ansi.

## <a name="when-not-to-use-pinvoke"></a>Kiedy nie używać PInvoke

Korzystanie z funkcji PInvoke nie jest odpowiednie dla wszystkich funkcji w stylu C w bibliotekach DLL. Załóżmy na przykład, że w pliku mylib.dll w pliku mylib.dll jest funkcja MakeSpecial zadeklarowana w następujący sposób:

`char * MakeSpecial(char * pszString);`

Jeśli używamy PInvoke w aplikacji Visual C++, możemy napisać coś podobnego do następującego:

```cpp
[DllImport("mylib")]
extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);
```

Trudność w tym miejscu jest to, że nie możemy usunąć pamięci dla ciągu niezarządzanego zwróconego przez MakeSpecial. Inne funkcje wywoływane za pośrednictwem PInvoke zwracają wskaźnik do buforu wewnętrznego, który nie musi być cofnięty przez użytkownika. W takim przypadku korzystanie z funkcji IJW jest oczywistym wyborem.

## <a name="limitations-of-pinvoke"></a>Ograniczenia PInvoke

Nie można zwrócić tego samego dokładnego wskaźnika z funkcji macierzystej, która została wchłoń jako parametr. Jeśli funkcja macierzysta zwraca wskaźnik, który został zorganizowany do niego przez PInvoke, uszkodzenie pamięci i wyjątki mogą wystąpić.

```cpp
__declspec(dllexport)
char* fstringA(char* param) {
   return param;
}
```

Poniższy przykład wykazuje ten problem i mimo że program może wydawać się dać poprawne dane wyjściowe, dane wyjściowe pochodzą z pamięci, która została zwolniona.

```cpp
// platform_invocation_services_5.cpp
// compile with: /clr /c
using namespace System;
using namespace System::Runtime::InteropServices;
#include <limits.h>

ref struct MyPInvokeWrap {
public:
   [ DllImport("user32.dll", EntryPoint = "CharLower", CharSet = CharSet::Ansi) ]
   static String^ CharLower([In, Out] String ^);
};

int main() {
   String ^ strout = "AabCc";
   Console::WriteLine(strout);
   strout = MyPInvokeWrap::CharLower(strout);
   Console::WriteLine(strout);
}
```

## <a name="marshaling-arguments"></a>Kierowanie argumentów

With `PInvoke`, nie jest potrzebne organizowanie między zarządzanych i C++ natywnych typów pierwotnych z tej samej formie. Na przykład nie jest wymagane kierowanie między Int32 i int lub między Double i double.

Jednak należy marszałka typów, które nie mają tego samego formularza. Obejmuje to typy char, string i struct. W poniższej tabeli przedstawiono mapowania używane przez organizatora dla różnych typów:

|wtypes.h|Visual C++|Visual C++ z /clr|Środowisko wykonawcze języka wspólnego|
|--------------|------------------|-----------------------------|-----------------------------|
|Obsługi|Void\*|Void\*|IntPtr, UIntPtr|
|BYTE|unsigned char|unsigned char|Byte|
|Krótki|short|short|Int16|
|WORD|unsigned short|unsigned short|UInt16|
|INT|int|int|Int32|
|UINT|unsigned int|unsigned int|UInt32|
|Długi|long|long|Int32|
|Bool|long|bool|Wartość logiczna|
|DWORD|unsigned long|unsigned long|UInt32|
|Ulong|unsigned long|unsigned long|UInt32|
|Char|char|char|Char|
|Lpstr|Char\*|String ^ [in], StringBuilder ^ [in, out]|String ^ [in], StringBuilder ^ [in, out]|
|LPCSTR|const char (char)\*|Ciąg ^|Ciąg|
|Lpwstr|Wchar_t\*|String ^ [in], StringBuilder ^ [in, out]|String ^ [in], StringBuilder ^ [in, out]|
|LPCWSTR (WZT|wchar_t\*|Ciąg ^|Ciąg|
|Float|float|float|Single|
|Podwójne|double|double|Double|

Organizator automatycznie przypina pamięć przydzieloną na stercie środowiska wykonawczego, jeśli jego adres jest przekazywany do funkcji niezarządzanej. Przypinanie uniemożliwia modułowi zbierającemu elementy bezużyteczne przenoszenie przydzielonego bloku pamięci podczas zagęszczania.

W przykładzie pokazanym wcześniej w tym temacie CharSet parametr DllImport określa, jak zarządzane ciągi powinny być organizowane; w takim przypadku powinny one być kierowane do ciągów ANSI dla strony macierzystej.

Można określić informacje o kierowaniu dla poszczególnych argumentów funkcji macierzystej przy użyciu atrybutu MarshalAs. Istnieje kilka opcji organizowania \* String argument: BStr, ANSIBStr, TBStr, LPStr, LPWStr i LPTStr. Wartość domyślna to LPStr.

W tym przykładzie ciąg jest organizowany jako ciąg znaków Unicode o podwójnym bajku, LPWStr. Wyjście jest pierwszą literą Hello World! ponieważ drugi bajt kierowanego ciągu ma wartość null i interpretuje to jako znacznik końca ciągu.

```cpp
// platform_invocation_services_3.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[DllImport("msvcrt", EntryPoint="puts")]
extern "C" int puts([MarshalAs(UnmanagedType::LPWStr)] String ^);

int main() {
   String ^ pStr = "Hello World!";
   puts(pStr);
}
```

Atrybut MarshalAs znajduje się w obszarze nazw System::Runtime::InteropServices. Atrybut może służyć z innymi typami danych, takimi jak tablice.

Jak wspomniano wcześniej w temacie, biblioteki kierowanie udostępnia nową, zoptymalizowaną metodę organizowania danych między środowiskami macierzystymi i zarządzanymi. Aby uzyskać więcej informacji, zobacz [Omówienie organizowania w języku C++](../dotnet/overview-of-marshaling-in-cpp.md).

## <a name="performance-considerations"></a>Zagadnienia dotyczące wydajności

PInvoke ma obciążenie między 10 i 30 x86 instrukcje na wywołanie. Oprócz tego kosztu stałego organizowanie tworzy dodatkowe obciążenie. Nie ma żadnych kosztów organizowania między typami blittable, które mają taką samą reprezentację w kodzie zarządzanym i niezarządzanym. Na przykład nie ma żadnych kosztów tłumaczenia między int i Int32.

Aby uzyskać lepszą wydajność, mają mniej PInvoke wywołania, że marshal jak najwięcej danych, jak to możliwe, zamiast więcej wywołań, które marshal mniej danych na wywołanie.

## <a name="see-also"></a>Zobacz też

[Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)
