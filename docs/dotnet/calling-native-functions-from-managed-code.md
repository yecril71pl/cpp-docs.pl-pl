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
ms.openlocfilehash: 50f40cc147daaa26a7fa4e607f0d4dd42cf22d61
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988665"
---
# <a name="calling-native-functions-from-managed-code"></a>Wywoływanie funkcji natywnych z kodu zarządzanego

Środowisko uruchomieniowe języka wspólnego (CLR) zapewnia platformę wywołania usług lub jako PInvoke, które umożliwia zarządzanemu kodowi wywoływanie funkcji w stylu C z macierzystych bibliotek łączonych dynamicznie (DLL). Takie samo szeregowanie danych jak dla współdziałania COM jest zastosowane dla środowiska uruchomieniowego dla „It Just Works,” lub mechanizmu IJW.

Aby uzyskać więcej informacji, zobacz:

- [Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)

- [Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

Przykłady w tym rozdziale jedynie ilustrują jak `PInvoke` może być zastosowany. `PInvoke` może uprościć serializację dostosowanych danych, ponieważ użytkownik podaje informacje dotyczące serializacji deklaratywnie w atrybutach zamiast wpisywać kod procedury serializacji.

> [!NOTE]
>  Biblioteka organizowania zawiera alternatywny sposób organizowania danych między środowiskami macierzystymi i zarządzanymi w sposób zoptymalizowany. Zobacz [Omówienie organizowania w programie C++ ](../dotnet/overview-of-marshaling-in-cpp.md) , aby uzyskać więcej informacji na temat biblioteki organizowania. Biblioteka organizatora jest przydatna tylko do danych, nie dla funkcji.

## <a name="pinvoke-and-the-dllimport-attribute"></a>Funkcja PInvoke i atrybut DllImport

Poniższy przykład pokazuje użycie klasy `PInvoke` w programie Visual C++. Umieszczenie funkcji macierzystej jest zdefiniowane w msvcrt.dll. Atrybut DllImport służy do deklaracji umieszczania.

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

Poniższy przykład jest równoważny poprzedniemu, ale używa IJW.

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

- Nie ma konieczności zapisywania deklaracji atrybutów `DLLImport` dla niezarządzanych API używanych przez program. Po prostu dołącz plik nagłówkowy i łącze z biblioteką importu.

- Mechanizm IJW jest trochę szybszy (na przykład fragmenty IJW nie muszą sprawdzać konieczności przypięcie lub skopiowania elementów danych, gdyż jest to jawnie wykonywane przez programistę).

- Wyraźnie pokazuje problemy z wydajnością. W tym przypadku użytkownik tłumaczy z ciągu Unicode na ciąg ANSI i posiada funkcję alokacji i dezalokacji pamięci pomocniczej. W tym przypadku projektant wpisujący kod za pomocą IJW zda sobie sprawę, że wywołanie `_putws` i wykorzystanie `PtrToStringChars` byłoby lepsze dla wydajności.

- Jeśli wywołasz wiele niezarządzanych interfejsów programowania aplikacji (API) przy użyciu tych samych danych, to zorganizowanie ich raz i przesłanie kopii zorganizowanej jest znacznie bardziej efektywne niż powtórne organizowanie za każdym razem.

### <a name="disadvantages-of-ijw"></a>Wady IJW

- Kierowanie musi być określona wyraźnie w kodzie, a nie przez atrybuty (które często mają odpowiednie wartości domyślne).

- Organizowanie kodu odbywa się wewnętrznie, gdzie jest bardziej inwazyjne w procesie logiki aplikacji.

- Ponieważ jawne kierujący interfejs API zwraca `IntPtr` typy przenośne 32-bitowej do 64-bitowe, należy użyć dodatkowych `ToPointer` wywołań.

Specjalna metoda eksponowana przez C++ jest bardziej wydajną metodą zewnętrzną kosztem dodatkowej złożoności.

Jeśli aplikacja wykorzystuje głównie niezarządzane typy danych lub jeśli wywołuje więcej niezarządzanych interfejsów API niż interfejsów API .NET Framework, zalecamy użycie funkcji IJW. Aby wywołać przypadkowy niezarządzany API w większości zarządzanej aplikacji, wybór jest bardziej subtelny.

## <a name="pinvoke-with-windows-apis"></a>Mechanizm PInvoke z interfejsami API systemu Windows

Mechanizm PInvoke jest wygodny w przypadku wywołania funkcji w systemie Windows.

W tym przykładzie program Visual C++ współdziała z funkcją MessageBox, która jest częścią interfejsu Win32 API.

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

Wynik to okno komunikatu z tytułem PInvoke Test zawierające tekst Witaj Świecie!

Informacje dotyczące organizowania są również używane przez PInvoke do wyszukiwania funkcji w bibliotece DLL. W bibliotece user32.dll nie ma w rzeczywistości funkcji MessageBox, ale element CharSet=CharSet::Ansi umożliwia włączenie funkcji PInvoke w celu użycia MessageBoxA, wersji ANSI zamiast MessageBoxW, która jest wersją Unicode. Ogólnie rzecz biorąc, zaleca się używanie wersje Unicode niezarządzanych interfejsów API, ponieważ eliminuje to narzut tłumaczenia z natywnego formatu Unicode obiektów ciągu .NET Framework do ANSI.

## <a name="when-not-to-use-pinvoke"></a>Kiedy nie należy używać PInvoke

korzystanie z PInvoke nie jest odpowiednie dla wszystkich funkcji stylu C w DLL. Załóżmy na przykład, że w bibliotece mylib.dll jest funkcja MakeSpecial, zadeklarowana w następujący sposób:

`char * MakeSpecial(char * pszString);`

Jeśli używamy funkcji PInvoke w aplikacji Visual C++, możemy napisać coś podobnego do:

```cpp
[DllImport("mylib")]
extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);
```

Trudność polega na tym, że firma Microsoft nie można usunąć pamięci dla niezarządzanego ciągu zwracanego przez MakeSpecial. Inne funkcje wywoływane za pośrednictwem funkcji PInvoke zwracają wskaźnik do wewnętrznego buforu, którego użytkownik nie musi odwołać. W tym przypadku korzystanie z funkcji IJW jest oczywistym wyborem.

## <a name="limitations-of-pinvoke"></a>Ograniczenia funkcji PInvoke

Nie można przywrócić dokładnie tego samego wskaźnika z funkcji natywnej, która została przyjęta jako parametr. Jeśli funkcja natywna zwraca wskaźnik, który został przekazany przez PInvoke, może pojawić się uszkodzenie pamięci i wyjątki.

```cpp
__declspec(dllexport)
char* fstringA(char* param) {
   return param;
}
```

Poniższy przykład ukazuje ten problem, a nawet, jeśli wydaje się, że program podaje poprawne dane wyjściowe, dane wyjściowe pochodzą z pamięci, która zostały uwolniona.

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

## <a name="marshaling-arguments"></a>Kierowanie argumentami

Dzięki `PInvoke`, nie jest konieczne szeregowanie między zarządzanymi i natywnymi prymitywnymi typami C++ o tej samej formie. Na przykład zarządzanie nie jest wymagane między Int32 a int lub między Double a double.

Jednakże musisz zarządzać typami, które nie mają tego samego formularza. Obejmuje to znaki, ciągi typy struktury. W poniższej tabeli przedstawiono mapowania używane przez organizatora dla różnych typów:

|wtypes.h|Visual C++|Visual C++ z /clr|Środowisko uruchomieniowe języka wspólnego|
|--------------|------------------|-----------------------------|-----------------------------|
|HANDLE|\* void|\* void|IntPtr, UIntPtr|
|BYTE|unsigned char|unsigned char|Byte|
|KRÓTKI|short|short|Int16|
|WORD|unsigned short|unsigned short|UInt16|
|INT|int|int|Int32|
|UINT|unsigned int|unsigned int|UInt32|
|LONG|long|long|Int32|
|BOOL|long|bool|Boolean|
|DWORD|unsigned long|unsigned long|UInt32|
|ULONG|unsigned long|unsigned long|UInt32|
|CHAR|char|char|Char|
|LPCSTR|\* char|String ^ [in], StringBuilder ^ [in, out]|String ^ [in], StringBuilder ^ [in, out]|
|LPCSTR|stała char \*|Ciąg ^|String|
|LPWSTR|wchar_t \*|String ^ [in], StringBuilder ^ [in, out]|String ^ [in], StringBuilder ^ [in, out]|
|LPCWSTR|stała wchar_t \*|Ciąg ^|String|
|ZWOLNIJ|float|float|Single|
|WARTOŚĆ DWUBAJTOWA|double|double|Double|

Organizator niestandardowy automatycznie przypina pamięć przydzieloną na stosie uruchomieniowym, jeśli adres jest przekazywany do niezarządzanej funkcji. Przypinanie zapobiega przenoszeniu przydzielonego bloku pamięci podczas kompaktowania przez mechanizmu odśmiecacza.

W przykładzie przedstawionym wcześniej w tym temacie, parametr CharSet elementu DllImport określa sposób, w jaki ciągi zarządzane powinny być wprowadzane; w tym przypadku powinny być wprowadzane do ciągów ANSI do strony natywnej.

Możesz określić szeregowanie informacji dla indywidualnych argumentów funkcji natywnej, używając atrybutu MarshalAs. Istnieje kilka opcji organizowania ciągu \* argument: BStr, ANSIBStr, TBStr, LPStr, LPWStr i LPTStr. Domyślna wartość to LPStr.

W tym przykładzie ciąg jest przekazywany jako ciąg dwubajtowych znaków Unicode, LPWStr. Dane wyjściowe są pierwszą literą Hello world! ponieważ drugi bajt ciągu organizowanego ma wartość null, a wartości są interpretowane jako znacznik końca ciągu.

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

Atrybut MarshalAs jest w obszarze nazw System::Runtime::InteropServices. Atrybut może być używany z innymi typami danych, takimi jak tablice.

Jak wspomniano wcześniej w temacie, kierująca biblioteka zawiera nową, zoptymalizowaną metodę przekazywania międzyprocesowego danych między środowiskami macierzystymi i zarządzanymi. Aby uzyskać więcej informacji, zobacz [Omówienie organizowania w programie C++ ](../dotnet/overview-of-marshaling-in-cpp.md).

## <a name="performance-considerations"></a>Uwagi dotyczące wydajności

Mechanizm PInvoke ma obciążenie ok. 10 i 30 x86 instrukcji przypadających na wywołanie. Oprócz tego kosztu stałego, przekazywania międzyprocesowe tworzą dodatkowe obciążenie. Nie ma kosztu szeregowania między danymi kopiowalnymi, które posiadają tę samą reprezentację w zarządzanym i niezarządzanym kodzie. Na przykład tłumaczenie z int na Int32 nie pociąga za sobą żadnych kosztów.

Aby poprawić wydajność, używaj mniejszej liczby wywołań funkcji PInvoke zarządzających jak największą ilością danych, zamiast większej liczby wywołań, które zarządzają mniejszą ilością danych na wywołanie.

## <a name="see-also"></a>Zobacz także

[Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)
