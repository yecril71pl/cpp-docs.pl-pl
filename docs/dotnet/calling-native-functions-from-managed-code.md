---
title: "Wywoływanie funkcji natywnych z kodu zarządzanego | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- native functions called from managed code [C++]
- managed code [C++], interoperability
- platform invoke [C++], interoperability
- interoperabiliy [C++], calling native functions from managed code
- calling native functions from managed code
- interop [C++], calling native functions from managed code
ms.assetid: 982cef18-20d9-42b4-8242-a77fa65f2e36
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 159b80fcc015db2999309fe99e9617f7dcd409ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="calling-native-functions-from-managed-code"></a>Wywoływanie funkcji natywnych z kodu zarządzanego
Środowisko uruchomieniowe języka wspólnego zapewnia usług wywołania platformy lub funkcji PInvoke, że umożliwia zarządzanego kodu do wywołania funkcji w stylu języka C w natywnej biblioteki łączone dynamicznie (dll). Organizowanie danych sam jest używany jak w przypadku współdziałania COM ze środowiskiem uruchomieniowym i mechanizmu "Ją po prostu działa" lub IJW.  
  
 Aby uzyskać więcej informacji, zobacz:  
  
-   [Używanie jawnej funkcji PInvoke w języku C++ (atrybut DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)  
  
-   [Korzystanie z międzyoperacyjności języka C++ (niejawna funkcja PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)  
  
-   [Bliższe spojrzenie na platformie wywołania](http://msdn.microsoft.com/en-us/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
  
 Próbek w tej sekcji po prostu przedstawiają sposób `PInvoke` mogą być używane. `PInvoke`można uprościć przekazywanie danych niestandardowych, ponieważ dostarcza informacji organizacyjnych deklaratywnie w atrybutach zamiast zapisywania procedurach kodu zestawiającego.  
  
> [!NOTE]
>  Biblioteka organizowania zapewnia alternatywny sposób organizowania danych między środowiskami natywne i zarządzane w sposób zoptymalizowane. Zobacz [omówienie z Marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md) Aby uzyskać więcej informacji na temat biblioteki marshalingu. Biblioteka marshalingu jest możliwe, tylko dane, a nie funkcji.  
  
## <a name="pinvoke-and-the-dllimport-attribute"></a>PInvoke i atrybut DllImport  
 W poniższym przykładzie przedstawiono użycie `PInvoke` w programie Visual C++. Naraża funkcji macierzystej jest zdefiniowany w msvcrt.dll. Atrybut DllImport jest używany dla deklaracji naraża.  
  
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
  
 Poniższy przykład jest odpowiednikiem powyższego przykładu, ale używają IJW.  
  
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
  
-   Nie istnieje potrzeba do zapisania `DLLImport` atrybutu deklaracji dla niezarządzane interfejsy API, będzie używana. Po prostu dołączyć plik nagłówka i Połącz z biblioteką importu.  
  
-   Mechanizm IJW jest nieco większą (na przykład klas zastępczych IJW nie trzeba sprawdzić konieczność numeru pin lub kopiowanie elementów danych, ponieważ jawnie wykonywane przez dewelopera).  
  
-   Go wyraźnie ilustruje problemy z wydajnością. W takim przypadku fakt, że są tłumaczenia z ciągiem Unicode do postaci ciągu ANSI i mieć alokacji pamięci towarzyszącej oraz cofania alokacji. W takim przypadku dewelopera pisanie kodu przy użyciu IJW czy należy pamiętać, tym wywołaniem `_putws` i przy użyciu `PtrToStringChars` byłoby lepszą wydajność.  
  
-   Jeśli wywołana wiele niezarządzane interfejsy API przy użyciu tych samych danych, przekazywanie go raz i przekazywanie organizowane kopia jest bardziej wydajne niż ponownie organizowanie zawsze.  
  
### <a name="disadvantages-of-ijw"></a>Wady IJW  
  
-   Organizowanie musi być określona jawnie w kodzie zamiast za atrybutów (które często mają odpowiednie ustawienia domyślne).  
  
-   Zawiera kod jest wbudowany, gdzie jest bardziej inwazyjne przepływu logiki aplikacji.  
  
-   Ponieważ zwraca jawne interfejsy API kierowania `IntPtr` typów przenośności 32-bitowej do 64-bitowych, należy użyć bardzo `ToPointer` wywołania.  
  
 Określona metoda udostępnianych przez C++ jest bardziej wydajne, jawne, kosztem niektórych stopnia złożoności.  
  
 Jeśli aplikacja używa głównie niezarządzanych danych typów lub jeśli wywołuje więcej niż interfejsów API architektury .NET Framework niezarządzane interfejsy API, zalecamy, aby funkcja IJW. Aby wywołać okazjonalne niezarządzanego API w aplikacji zarządzanej przede wszystkim, wybór jest aspekty.  
  
## <a name="pinvoke-with-windows-apis"></a>PInvoke z interfejsów API systemu Windows  
 PInvoke jest wygodną metodą wywoływanie funkcji w systemie Windows.  
  
 W tym przykładzie programu Visual C++ współdziała z funkcji MessageBox, która jest częścią interfejsu API systemu Win32.  
  
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
  
 Dane wyjściowe to okno komunikatu pod tytułem PInvoke testu, który zawiera tekst Hello World!.  
  
 Dane kierowania służy także PInvoke do odszukania funkcji w bibliotece DLL. User32.dll na dysku jest w rzeczywistości nie MessageBox funkcji, ale CharSet = CharSet::Ansi włączenie funkcji PInvoke do używania MessageBoxA, wersji ANSI, zamiast MessageBoxW, który jest wersją Unicode. Ogólnie rzecz biorąc zalecane jest użycie wersji Unicode niezarządzane interfejsy API, która eliminuje tłumaczenia nakłady pracy związane z natywnego formatu Unicode obiektów string .NET Framework do strony kodowej ANSI.  
  
## <a name="when-not-to-use-pinvoke"></a>Kiedy nie należy używać funkcji PInvoke  
 Za pomocą funkcji PInvoke nie jest odpowiedni dla wszystkich funkcji w stylu języka C w bibliotekach DLL. Na przykład załóżmy, że jest funkcją MakeSpecial w mylib.dll zadeklarowany w następujący sposób:  
  
 `char * MakeSpecial(char * pszString);`  
  
 Czy możemy użyć funkcji PInvoke w aplikacji Visual C++, firma Microsoft może zapisać podobny do następującego:  
  
 `[DllImport("mylib")]`  
  
 `extern "C" String * MakeSpecial([MarshalAs(UnmanagedType::LPStr)] String ^);`  
  
 Trudności w tym miejscu jest nie można usunąć pamięci do niezarządzanego zwrócony przez MakeSpecial ciąg. Innych funkcji wywołanych za pomocą funkcji PInvoke zwraca wskaźnik do wewnętrznego buforu, który nie ma przydzielenia przez użytkownika. W takim przypadku funkcja IJW jest wybór oczywiste.  
  
## <a name="limitations-of-pinvoke"></a>Ograniczenia funkcji PInvoke  
 Nie może zwracać wskaźnik dokładnie tego samego w funkcji natywnej trwało jako parametr. Jeśli funkcji macierzystej zwraca wskaźnik organizowanego do niej przez PInvoke, może nastąpić uszkodzenie pamięci i wyjątki.  
  
```  
__declspec(dllexport)  
char* fstringA(char* param) {  
   return param;  
}  
```  
  
 Poniższy przykład wykazuje ten problem, a nawet, jeśli program może wydawać się, aby zapewnić poprawne dane wyjściowe, dane wyjściowe pochodzące ze pamięci, która ma zostać zwolniony.  
  
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
  
## <a name="marshaling-arguments"></a>Przekazywanie argumentów  
 Z `PInvoke`, organizowanie nie jest niezbędne między zarządzane i typy pierwotne natywnych języka C++ z tego samego formularza. Na przykład organizowanie nie jest wymagany między Int32 i int lub między o podwójnej precyzji i o podwójnej precyzji.  
  
 Jednak należy kierować typów, które nie mają tego samego formularza. W tym typy char, string i struktury. W poniższej tabeli przedstawiono używane przez organizatora dla różnych typów mapowania:  
  
|wtypes.h|Visual C++|Visual C++ z/CLR|Środowisko uruchomieniowe języka wspólnego|  
|--------------|------------------|-----------------------------|-----------------------------|  
|DOJŚCIE|void *|void *|IntPtr i UIntPtr|  
|BYTE|unsigned char|unsigned char|Byte|  
|KRÓTKI|short|short|Int16|  
|WORD|unsigned short|unsigned short|UInt16|  
|INT|int|int|Int32|  
|UINT|unsigned int|unsigned int|UInt32|  
|DŁUGA|long|long|Int32|  
|WARTOŚĆ LOGICZNA|long|bool|Boolean|  
|DWORD|unsigned long|unsigned long|UInt32|  
|ULONG|unsigned long|unsigned long|UInt32|  
|CHAR|char|char|Char|  
|LPCSTR|char *|String ^ [in], StringBuilder ^ [w, limit]|String ^ [in], StringBuilder ^ [w, limit]|  
|LPCSTR|Const char *|String ^|String|  
|LPWSTR|wchar_t *|String ^ [in], StringBuilder ^ [w, limit]|String ^ [in], StringBuilder ^ [w, limit]|  
|LPCWSTR|Const wchar_t *|String ^|String|  
|FLOAT|float|float|Single|  
|O PODWÓJNEJ PRECYZJI|double|double|Double|  
  
 Organizator PIN automatycznie pamięci przydzielony na stosie środowiska uruchomieniowego, jeśli jego adres zostanie przekazany do funkcji niezarządzanej. Przypinanie uniemożliwia przenoszenie przydzielony blok pamięci podczas kompaktowania moduł garbage collector.  
  
 W przykładzie przedstawionym wcześniej w tym temacie, parametr CharSet DllImport określa zarządzanych ciągi powinny być przekazywane; w takim przypadku powinny być przekazywane do ciągów ANSI dla natywnych po stronie.  
  
 Można określić informacji organizacyjnych dla poszczególnych argumentów funkcji macierzystej przy użyciu atrybutu MarshalAs. Istnieje kilka opcji kierowanie ciągu * argument: BStr, ANSIBStr, TBStr, LPStr, LPWStr i LPTStr. Wartość domyślna to LPStr.  
  
 W tym przykładzie ten ciąg jest przekazywane jako ciąg znaków dwubajtowych Unicode, LPWStr. Dane wyjściowe jest pierwszą literę Hello World! ponieważ drugi bajt organizowane ciąg ma wartość null, a następnie umieszcza interpretuje jako znacznik końcowy ciągu.  
  
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
  
 Atrybut MarshalAs jest w przestrzeni nazw System::Runtime::InteropServices. Ten atrybut można z innych typów danych, takich jak tablic.  
  
 Jak wspomniano wcześniej w temacie, biblioteki marshalingu udostępnia nową, zoptymalizowaną metodę przekazywanie danych pomiędzy środowiskach natywnych i zarządzanych. Aby uzyskać więcej informacji, zobacz [omówienie z Marshalingu w języku C++](../dotnet/overview-of-marshaling-in-cpp.md).  
  
## <a name="performance-considerations"></a>Zagadnienia dotyczące wydajności  
 PInvoke ma obciążenie związane z zakresu od 10 do 30 x86 instrukcji na połączenie. Oprócz tego koszt stały organizowanie tworzy dodatkowe obciążenie. Nie ma żadnych kosztów kierowania między typy kopiowalne, które mają taką samą reprezentację w kodzie zarządzane i niezarządzane. Na przykład jest bezpłatna do tłumaczenia int i Int32.  
  
 W celu poprawy wydajności ma mniejszą liczbę wywołań PInvoke kierować jak najwięcej danych, jak to możliwe, zamiast kolejnych wywołań, które kierować mniejszej ilości danych na wywołanie.  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie natywne i .NET](../dotnet/native-and-dotnet-interoperability.md)