---
title: Wywoływanie funkcji natywnych z kodu zarządzanego | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- native functions called from managed code [C++]
- managed code [C++], interoperability
- platform invoke [C++], interoperability
- interoperabiliy [C++], calling native functions from managed code
- calling native functions from managed code
- interop [C++], calling native functions from managed code
ms.assetid: 982cef18-20d9-42b4-8242-a77fa65f2e36
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a220f0dc2c979676ad2e28fd504ef80e0925f74d
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/29/2018
ms.locfileid: "43195691"
---
# <a name="calling-native-functions-from-managed-code"></a>Wywoływanie funkcji natywnych z kodu zarządzanego
Środowisko uruchomieniowe języka wspólnego zapewnia platformę wywołania usług lub jako PInvoke, które umożliwia zarządzanemu kodowi można wywoływać funkcje w stylu języka C z macierzystych bibliotek łączonych dynamicznie (dll). Takie samo szeregowanie danych jest używany jak dla współdziałania COM ze środowiskiem uruchomieniowym i dla "It Just Works", lub mechanizmu IJW.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
-   [Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [Im bliżej wywołania platformy](https://msdn.microsoft.com/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
  
 Przykłady w tym rozdziale jedynie ilustrują jak `PInvoke` mogą być używane. `PInvoke` może uprościć serializację dostosowanych danych, ponieważ użytkownik podaje informacje dotyczące serializacji deklaratywnie w atrybutach zamiast wpisywać kod procedury.  
  
> [!NOTE]
>  Biblioteka organizowania zawiera alternatywny sposób organizowania danych między środowiskami macierzystymi i zarządzanymi w sposób zoptymalizowany. Zobacz [Overview of Marshaling w C++](../dotnet/overview-of-marshaling-in-cpp.md) Aby uzyskać więcej informacji dotyczących biblioteki masrhaling. Biblioteka organizatora jest przydatna, tylko do danych, a nie funkcji.  
  
## <a name="pinvoke-and-the-dllimport-attribute"></a>Funkcja PInvoke i atrybut DllImport  
 Poniższy przykład pokazuje użycie `PInvoke` w programie Visual C++. Funkcji macierzystej jest zdefiniowane w msvcrt.dll. Atrybut DllImport służy do deklaracji umieszczania.  
  
```  
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
  
```  
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
  
-   Nie ma konieczności zapisywania `DLLImport` atrybutu deklaracji dla niezarządzanych API używanych przez program. Po prostu Dołącz plik nagłówkowy i łącze z biblioteką importu.  
  
-   Mechanizm IJW jest trochę szybszy (na przykład wycinków IJW nie musi sprawdzać konieczności przypięcie lub skopiowania elementów danych ponieważ jawnie wykonywane przez dewelopera).  
  
-   Wyraźnie pokazuje problemy z wydajnością. W tym przypadku fakt, że tłumaczy z ciągu Unicode na ciąg ANSI i mieć towarzyszącej alokacji i dezalokacji pamięci. W tym przypadku Projektant wpisujący kod za pomocą IJW zda sobie sprawę, że wywołanie `_putws` i przy użyciu `PtrToStringChars` byłoby lepsze dla wydajności.  
  
-   Jeśli wywołasz wiele niezarządzanych interfejsów API przy użyciu tych samych danych zorganizowanie ich raz i przesłanie kopii zorganizowanej jest znacznie bardziej efektywne niż powtórne organizowanie za każdym razem.  
  
### <a name="disadvantages-of-ijw"></a>Wady IJW  
  
-   Kierowanie musi być określona wyraźnie w kodzie, a nie przez atrybuty (które często mają odpowiednie wartości domyślne).  
  
-   Organizowanie kodu jest w tekście, gdzie jest bardziej inwazyjne w procesie logiki aplikacji.  
  
-   Ponieważ jawne organizowania interfejsy API zwracają `IntPtr` typów przenośności 32-bitowej do 64-bitowych, należy użyć dodatkowych `ToPointer` wywołania.  
  
 Określonej metody udostępnianych przez C++ jest bardziej wydajną metodą, kosztem dodatkowej złożoności.  
  
 Jeśli aplikacja wykorzystuje głównie niezarządzane typy danych lub jeśli wywołuje więcej niezarządzanych interfejsów API niż interfejsów API programu .NET Framework, zalecane jest użycie funkcji IJW. Aby wywołać przypadkowy niezarządzany API w większości zarządzanej aplikacji, wybór jest bardziej subtelny.  
  
## <a name="pinvoke-with-windows-apis"></a>Mechanizm PInvoke z interfejsami API Windows  
 Mechanizm PInvoke jest wygodny w przypadku wywołania funkcji w Windows.  
  
 W tym przykładzie program Visual C++ współdziała z funkcją MessageBox, która jest częścią interfejsu Win32 API.  
  
```  
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
  
 Wynik to okno komunikatu, tytułem PInvoke Test, który zawiera tekst Witaj, świecie!.  
  
 Informacje dotyczące organizowania jest również używane przez PInvoke do wyszukiwania funkcji w bibliotece DLL. W bibliotece user32.dll nie jest w rzeczywistości nie funkcji MessageBox, ale CharSet = Charset:: ANSI umożliwia funkcji PInvoke w celu użycia MessageBoxA, wersji ANSI zamiast MessageBoxW, która jest wersją Unicode. Ogólnie rzecz biorąc zaleca się używanie wersje Unicode niezarządzanych interfejsów API, ponieważ eliminuje to narzut tłumaczenia z natywnego formatu Unicode obiektów ciągu .NET Framework do ANSI.  
  
## <a name="when-not-to-use-pinvoke"></a>Kiedy nie należy używać PInvoke  
 Za pomocą funkcji PInvoke nie jest odpowiednie dla wszystkich funkcji stylu C w dll. Na przykład załóżmy, że jest funkcja MakeSpecial w mylib.dll zadeklarowana w następujący sposób:  
  
 `char * MakeSpecial(char * pszString);`  
  
 Jeśli używamy funkcji PInvoke w aplikacji Visual C++, możemy napisać coś podobnego do następującego:  
  
 `[DllImport("mylib")]`  
  
 `extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);`  
  
 Trudności w tym miejscu jest, że firma Microsoft nie można usunąć pamięci dla niezarządzanego ciągu zwracanego przez MakeSpecial. Inne funkcje wywoływane za pośrednictwem funkcji PInvoke zwracają wskaźnik do wewnętrznego buforu, którego nie będzie musiał zostać cofnięta przez użytkownika. W tym przypadku korzystanie z funkcji IJW jest oczywistym wyborem.  
  
## <a name="limitations-of-pinvoke"></a>Ograniczenia funkcji PInvoke  
 Nie można zwrócić dokładnie tego samego wskaźnika z funkcji natywnej, która została przyjęta jako parametr. Jeśli funkcja natywna zwraca wskaźnik, który został przekazany do niego przez PInvoke, może nastąpić uszkodzenie pamięci i wyjątków.  
  
```  
__declspec(dllexport)  
char* fstringA(char* param) {  
   return param;  
}  
```  
  
 Poniższy przykład ukazuje ten problem, a mimo że program może wydawać się, aby zapewnić poprawne dane wyjściowe, dane wyjściowe pochodzą z pamięci, która zostały uwolniona.  
  
```  
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
 Za pomocą `PInvoke`, nie jest konieczne szeregowanie między zarządzanymi i natywnymi prymitywnymi typami C++ za pomocą tego samego formularza. Na przykład zarządzanie nie jest wymagane między Int32 a int lub między Double a double.  
  
 Jednakże musisz zarządzać typami, które nie mają tego samego formularza. Obejmuje to typy char, string i struktury. W poniższej tabeli przedstawiono mapowania używane przez organizatora dla różnych typów:  
  
|wtypes.h|Visual C++|Visual C++ z/CLR|Środowisko uruchomieniowe języka wspólnego|  
|--------------|------------------|-----------------------------|-----------------------------|  
|UCHWYT|Void \*|Void \*|IntPtr i UIntPtr|  
|BYTE|unsigned char|unsigned char|Byte|  
|KRÓTKA|short|short|Int16|  
|WORD|unsigned short|unsigned short|UInt16|  
|INT|int|int|Int32|  
|UINT|unsigned int|unsigned int|UInt32|  
|DŁUGI|long|long|Int32|  
|WARTOŚĆ LOGICZNA|long|bool|Boolean|  
|DWORD|unsigned long|unsigned long|UInt32|  
|ULONG|unsigned long|unsigned long|UInt32|  
|CHAR|char|char|Char|  
|LPCSTR|Char \*|String ^ [in], StringBuilder ^ [w, zewnętrzne]|String ^ [in], StringBuilder ^ [w, zewnętrzne]|  
|LPCSTR|Const char \*|String ^|String|  
|LPWSTR|wchar_t \*|String ^ [in], StringBuilder ^ [w, zewnętrzne]|String ^ [in], StringBuilder ^ [w, zewnętrzne]|  
|LPCWSTR|Const wchar_t \*|String ^|String|  
|FLOAT|float|float|Single|  
|PODWÓJNE|double|double|Double|  
  
 Organizator niestandardowy automatycznie Przypina pamięć przydzieloną na stosie uruchomieniowym, jeśli adres jest przekazywany do niezarządzanej funkcji. Przypinanie Zapobiega przenoszeniu przydzielonego bloku pamięci podczas kompaktowania przez mechanizmu moduł odśmiecania pamięci.  
  
 W przykładzie przedstawionym wcześniej w tym temacie, parametr CharSet elementu DllImport określa sposób zarządzane ciągi powinny być wprowadzane; w tym przypadku powinny być wprowadzane do ciągów ANSI do strony natywnej.  
  
 Możesz określić szeregowanie informacji dla indywidualnych argumentów funkcji natywnej, używając atrybutu MarshalAs. Istnieje kilka możliwości ciągu \* argumentu: BStr, ANSIBStr, TBStr, LPStr, LPWStr oraz LPTStr. Domyślna wartość to LPStr.  
  
 W tym przykładzie ciąg jest przekazywany jako ciąg znaków dwubajtowych Unicode, LPWStr. Dane wyjściowe to pierwsza litera Witaj, świecie! ponieważ drugi bajt uszeregowanego ciągu ma wartość null, a następnie umieszcza interpretuje to jako znacznik koniec ciągu.  
  
```  
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
  
 Atrybut MarshalAs jest w obszarze nazw System::Runtime:: InteropServices. Ten atrybut może służyć z innymi typami danych, takich jak tablice.  
  
 Jak wspomniano wcześniej w temacie, kierująca biblioteka zawiera nową, zoptymalizowaną metodę przekazywania międzyprocesowego danych między środowiskami macierzystymi i zarządzanymi. Aby uzyskać więcej informacji, zobacz [Overview of Marshaling w C++](../dotnet/overview-of-marshaling-in-cpp.md).  
  
## <a name="performance-considerations"></a>Zagadnienia dotyczące wydajności  
 Mechanizm PInvoke ma obciążenie z zakresu od 10 do 30 x86 instrukcji przypadających na wywołanie. Oprócz tego kosztu stałego, przekazywania międzyprocesowe tworzą dodatkowe obciążenie. Nie ma kosztu szeregowania między danymi kopiowalnymi, które mają tę samą reprezentację w kodzie zarządzanym i niezarządzanym. Na przykład jest bezpłatne tłumaczenie z int i Int32.  
  
 Lepszą wydajność należy mieć mniejszej liczby wywołań funkcji PInvoke zarządzających jak najwięcej danych, jak to możliwe, zamiast większej liczby wywołań, które zarządzają mniejszą ilością danych na wywołanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)