---
title: Operacje Windows (C + +/ CLI) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Windows [C++], Windows-specific tasks
- .NET Framework [C++], Windows operations
- Visual C++, Windows operations
- Windows operations [C++]
- .NET Framework, shutdown
- shutdown
- termination
- applications [C++], shutdown
- Visual C++, user interactive state
- user interactive state
- Visual C++, reading from Windows Registry
- registry, reading
- performance counters
- performance counters, reading Windows performance counters
- performance monitoring, Windows performance counters
- performance, counters
- counters, reading Windows performance counters
- performance
- performance monitoring
- text, retrieving from Clipboard
- Clipboard, retrieving text
- current user names
- user names, retrieving
- UserName string
- .NET Framework, version
- Version property, retrieving .NET Framework version
- computer name, retrieving
- machine name, retrieving
- computer name
- Windows [C++], version
- Windows [C++], retrieving version using Visual C++
- time, elapsed since startup
- counters, elapsed time
- startup, time elapsed since
- tick counts
- startup
- text, storing in Clipboard
- Clipboard, storing text
- registry, writing to
- Visual C++, writing to Windows Registry
ms.assetid: b9a75cb4-0589-4d5b-92cb-5e8be42b4ac0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 0f9566fb6e3117b10d0d6f4a2bccbe56fe33a28a
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2018
ms.locfileid: "42609352"
---
# <a name="windows-operations-ccli"></a>Operacje związane z systemem Windows (C++/CLI)
Demonstruje różne zadania specyficzne dla Windows przy użyciu zestawu Windows SDK.  
  
 W poniższych tematach pokazano różne operacje Windows wykonywana przy użyciu zestawu SDK Windows, przy użyciu języka Visual C++.  

## <a name="determine_shutdown"></a> Określić, czy rozpoczęło
Poniższy przykład kodu demonstruje sposób określania, czy aplikacji lub .NET Framework jest obecnie przerywa. Jest to przydatne do uzyskiwania dostępu do statycznych elementów w .NET Framework, ponieważ podczas zamykania systemu, te konstrukcje sfinalizowaniu przez system i nie można niezawodnie. Sprawdzając <xref:System.Environment.HasShutdownStarted%2A> właściwość najpierw można uniknąć potencjalnych błędów, nie dostęp do tych elementów.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// check_shutdown.cpp  
// compile with: /clr  
using namespace System;  
int main()   
{  
   if (Environment::HasShutdownStarted)  
      Console::WriteLine("Shutting down.");  
   else  
      Console::WriteLine("Not shutting down.");  
   return 0;  
}  
```  

## <a name="determine_user"></a> Określanie stanu interaktywności użytkownika
Poniższy przykład kodu pokazuje, jak ustalić, czy kod jest uruchamiany w kontekście interakcji z użytkownikiem. Jeśli <xref:System.Environment.UserInteractive%2A> ma wartość FAŁSZ, a następnie kod działa jako proces usługi lub od wewnątrz aplikacji sieci Web, w którym to przypadku należy zrezygnować do interakcji z użytkownikiem.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// user_interactive.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   if ( Environment::UserInteractive )  
      Console::WriteLine("User interactive");  
   else  
      Console::WriteLine("Noninteractive");  
   return 0;  
}  
```  

## <a name="read_registry"></a> Odczytywanie danych z rejestru Windows
Poniższy przykład kodu wykorzystuje <xref:Microsoft.Win32.Registry.CurrentUser> klucza do odczytywania danych z rejestru Windows. Najpierw podkluczy wyliczane są przy użyciu <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> metody, a następnie podklucz tożsamości jest otwierane przy użyciu <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> metody. Takie jak klucze główne każdy jest reprezentowany przez <xref:Microsoft.Win32.RegistryKey> klasy. Ponadto nowe <xref:Microsoft.Win32.RegistryKey> obiekt jest używany do wyliczenia pary klucz/wartość.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// registry_read.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main( )  
{  
   array<String^>^ key = Registry::CurrentUser->GetSubKeyNames( );  
  
   Console::WriteLine("Subkeys within CurrentUser root key:");  
   for (int i=0; i<key->Length; i++)  
   {  
      Console::WriteLine("   {0}", key[i]);  
   }  
  
   Console::WriteLine("Opening subkey 'Identities'...");  
   RegistryKey^ rk = nullptr;  
   rk = Registry::CurrentUser->OpenSubKey("Identities");  
   if (rk==nullptr)  
   {  
      Console::WriteLine("Registry key not found - aborting");  
      return -1;  
   }  
  
   Console::WriteLine("Key/value pairs within 'Identities' key:");  
   array<String^>^ name = rk->GetValueNames( );  
   for (int i=0; i<name->Length; i++)  
   {  
      String^ value = rk->GetValue(name[i])->ToString();  
      Console::WriteLine("   {0} = {1}", name[i], value);  
   }  
  
   return 0;  
}  
```  
  
### <a name="remarks"></a>Uwagi  
 <xref:Microsoft.Win32.Registry> Klasy jest jedynie kontenerem dla statycznych wystąpień <xref:Microsoft.Win32.RegistryKey>. Każde wystąpienie reprezentuje węzeł główny rejestru. Wystąpienia są <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine>, i <xref:Microsoft.Win32.Registry.Users>.  
  
 Ponadto aby są statyczne, obiekty w ramach <xref:Microsoft.Win32.Registry> klasy są przeznaczone tylko do odczytu. Ponadto wystąpienia elementu <xref:Microsoft.Win32.RegistryKey> klasę, która są tworzone w celu dostępu do zawartości rejestru obiektów, również są przeznaczone tylko do odczytu. Na przykład sposób zastąpienia tego zachowania, zobacz [jak: zapisu danych do rejestru Windows (C + +/ CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md).  
  
 Istnieją dwa dodatkowe obiekty w <xref:Microsoft.Win32.Registry> klasy: <xref:Microsoft.Win32.Registry.DynData> i <xref:Microsoft.Win32.Registry.PerformanceData>. Oba są wystąpieniami <xref:Microsoft.Win32.RegistryKey> klasy. <xref:Microsoft.Win32.Registry.DynData> Obiekt zawiera informacje rejestru dynamicznych, która jest obsługiwana tylko w Windows 98 i Windows Me. <xref:Microsoft.Win32.Registry.PerformanceData> Obiekt może służyć do uzyskania dostępu do aplikacji, które używają systemu monitorowania wydajności Windows, informacje o liczniku wydajności. <xref:Microsoft.Win32.Registry.PerformanceData> Węzeł reprezentuje informacje, które faktycznie nie są przechowywane w rejestrze i w związku z tym nie można wyświetlić za pomocą Regedit.exe.  

## <a name="read_performance"></a> Odczytywanie liczników wydajności Windows
Niektóre aplikacje i podsystemy Windows ujawnić dane wydajności za pośrednictwem wydajności systemu Windows. Te liczniki są dostępne za pomocą <xref:System.Diagnostics.PerformanceCounterCategory> i <xref:System.Diagnostics.PerformanceCounter> klasy, które znajdują się w <xref:System.Diagnostics?displayProperty=fullName> przestrzeni nazw.  
  
 Poniższy przykład kodu używa tych klas należy pobrać i wyświetlić licznika, która jest aktualizowana przez Windows, aby wskazać wartość procentowa czasu procesora jest zajęty.  
  
> [!NOTE]
>  W tym przykładzie wymaga uprawnień administracyjnych do uruchamiania w systemie Windows Vista.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// processor_timer.cpp  
// compile with: /clr  
#using <system.dll>  
  
using namespace System;  
using namespace System::Threading;  
using namespace System::Diagnostics;  
using namespace System::Timers;  
  
ref struct TimerObject  
{  
public:  
   static String^ m_instanceName;  
   static PerformanceCounter^ m_theCounter;  
  
public:  
   static void OnTimer(Object^ source, ElapsedEventArgs^ e)  
   {  
      try   
      {  
         Console::WriteLine("CPU time used: {0,6} ",  
          m_theCounter->NextValue( ).ToString("f"));  
      }   
      catch(Exception^ e)  
      {  
         if (dynamic_cast<InvalidOperationException^>(e))  
         {  
            Console::WriteLine("Instance '{0}' does not exist",  
                  m_instanceName);  
            return;  
         }  
         else  
         {  
            Console::WriteLine("Unknown exception... ('q' to quit)");  
            return;  
         }  
      }  
   }  
};  
  
int main()  
{  
   String^ objectName = "Processor";  
   String^ counterName = "% Processor Time";  
   String^ instanceName = "_Total";  
  
   try  
   {  
      if ( !PerformanceCounterCategory::Exists(objectName) )  
      {  
         Console::WriteLine("Object {0} does not exist", objectName);  
         return -1;  
      }  
   }  
   catch (UnauthorizedAccessException ^ex)  
   {  
      Console::WriteLine("You are not authorized to access this information.");  
      Console::Write("If you are using Windows Vista, run the application with ");  
      Console::WriteLine("administrative privileges.");  
      Console::WriteLine(ex->Message);  
      return -1;  
   }  
  
   if ( !PerformanceCounterCategory::CounterExists(  
          counterName, objectName) )  
   {  
      Console::WriteLine("Counter {0} does not exist", counterName);  
      return -1;  
   }  
  
   TimerObject::m_instanceName = instanceName;  
   TimerObject::m_theCounter = gcnew PerformanceCounter(  
          objectName, counterName, instanceName);  
  
   System::Timers::Timer^ aTimer = gcnew System::Timers::Timer();  
   aTimer->Elapsed += gcnew ElapsedEventHandler(&TimerObject::OnTimer);  
   aTimer->Interval = 1000;  
   aTimer->Enabled = true;  
   aTimer->AutoReset = true;  
  
   Console::WriteLine("reporting CPU usage for the next 10 seconds");  
   Thread::Sleep(10000);  
   return 0;  
}  
```  

## <a name="retrieve_text"></a> Pobieranie tekstu ze Schowka
Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> funkcja elementu członkowskiego zwraca wskaźnik do <xref:System.Windows.Forms.IDataObject> interfejsu. Ten interfejs może następnie zapytań dla formatu danych i służy do pobierania danych rzeczywistych.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// read_clipboard.cpp  
// compile with: /clr  
#using <system.dll>  
#using <system.Drawing.dll>  
#using <system.windows.forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
  
[STAThread] int main( )  
{  
   IDataObject^ data = Clipboard::GetDataObject( );  
  
   if (data)  
   {  
      if (data->GetDataPresent(DataFormats::Text))   
      {  
         String^ text = static_cast<String^>  
           (data->GetData(DataFormats::Text));  
         Console::WriteLine(text);   
      }  
      else  
         Console::WriteLine("Nontext data is in the Clipboard.");  
   }  
   else   
   {  
      Console::WriteLine("No data was found in the Clipboard.");  
   }  
  
   return 0;  
}  
```  

## <a name="retrieve_current"></a> Pobieranie bieżącej nazwy użytkownika
Poniższy przykład kodu demonstruje pobieranie bieżącej nazwy użytkownika (nazwę użytkownika zalogowanego na Windows). Nazwa jest przechowywana w <xref:System.Environment.UserName%2A> ciąg, który jest zdefiniowany w <xref:System.Environment> przestrzeni nazw.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// username.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   Console::WriteLine("\nCurrent user: {0}", Environment::UserName);  
   return 0;  
}  
```  

## <a name="retrieve_dotnet"></a> Pobieranie wersji programu .NET Framework
Poniższy przykład kodu pokazuje, jak można określić wersji zainstalowanego środowiska .NET Framework z <xref:System.Environment.Version%2A> właściwość, która jest wskaźnikiem do <xref:System.Version> obiekt, który zawiera informacje o wersji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// dotnet_ver.cpp  
// compile with: /clr  
using namespace System;  
int main()   
{  
   Version^ version = Environment::Version;  
   if (version)  
   {  
      int build = version->Build;  
      int major = version->Major;  
      int minor = version->Minor;  
      int revision = Environment::Version->Revision;  
      Console::Write(".NET Framework version: ");  
      Console::WriteLine("{0}.{1}.{2}.{3}",   
            build, major, minor, revision);  
   }  
   return 0;  
}  
```  

## <a name="retrieve_local"></a> Pobieranie nazwy komputera lokalnego 
Poniższy przykład kodu demonstruje pobieranie nazwy komputera lokalnego (nazwa komputera w postaci, w jakiej jest wyświetlana w sieci). Osiągniesz to uzyskując <xref:System.Environment.MachineName%2A> ciąg, który jest zdefiniowany w <xref:System.Environment> przestrzeni nazw.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// machine_name.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   Console::WriteLine("\nMachineName: {0}", Environment::MachineName);  
   return 0;  
}  
```  

## <a name="retrieve_version"></a> Pobieranie wersji Windows
Poniższy przykład kodu pokazuje, jak można pobrać informacji o platformy i wersji bieżącego systemu operacyjnego. Te informacje są przechowywane w <xref:System.Environment.OSVersion%2A?displayProperty=fullName> właściwości i składa się z wyliczeniem, opisujący wersję Windows w warunkach szerokiego i <xref:System.Environment.Version%2A> obiekt, który zawiera dokładnie kompilacji systemu operacyjnego.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// os_ver.cpp  
// compile with: /clr  
using namespace System;  
  
int main()   
{  
   OperatingSystem^ osv = Environment::OSVersion;  
   PlatformID id = osv->Platform;  
   Console::Write("Operating system: ");  
  
   if (id == PlatformID::Win32NT)  
      Console::WriteLine("Win32NT");  
   else if (id == PlatformID::Win32S)  
      Console::WriteLine("Win32S");  
   else if (id == PlatformID::Win32Windows)  
      Console::WriteLine("Win32Windows");  
   else  
      Console::WriteLine("WinCE");  
  
   Version^ version = osv->Version;  
   if (version)  
   {  
      int build = version->Build;  
      int major = version->Major;  
      int minor = version->Minor;  
      int revision = Environment::Version->Revision;  
      Console::Write("OS Version: ");  
      Console::WriteLine("{0}.{1}.{2}.{3}",   
                   build, major, minor, revision);  
   }  
  
   return 0;  
}  
```  

## <a name="retrieve_time"></a> Pobieranie czasu, jaki upłynął od uruchomienia
Poniższy przykład kodu pokazuje, jak określić liczbę cykli lub liczbę milisekund, które upłynęły od Windows została uruchomiona. Ta wartość jest przechowywana w <xref:System.Environment.TickCount%2A?displayProperty=fullName> elementu członkowskiego i, ponieważ jest wartością 32-bitową, przywraca zero co 24,9 dni.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// startup_time.cpp  
// compile with: /clr  
using namespace System;  
  
int main( )   
{  
   Int32 tc = Environment::TickCount;  
   Int32 seconds = tc / 1000;  
   Int32 minutes = seconds / 60;  
   float hours = static_cast<float>(minutes) / 60;  
   float days = hours / 24;  
  
   Console::WriteLine("Milliseconds since startup: {0}", tc);  
   Console::WriteLine("Seconds since startup: {0}", seconds);  
   Console::WriteLine("Minutes since startup: {0}", minutes);  
   Console::WriteLine("Hours since startup: {0}", hours);  
   Console::WriteLine("Days since startup: {0}", days);  
  
   return 0;  
}  
```  

## <a name="store_text"></a> Store tekstu w Schowku
Poniższy przykład kodu wykorzystuje <xref:System.Windows.Forms.Clipboard> obiektu zdefiniowany w <xref:System.Windows.Forms> przestrzeni nazw do przechowywania ciągu. Ten obiekt zawiera dwie funkcje Członkowskie: <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> i <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>. Dane są przechowywane w Schowku, wysyłając dowolnego obiektu pochodzącego z <xref:System.Object> do <xref:System.Windows.Forms.Clipboard.SetDataObject%2A>.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// store_clipboard.cpp  
// compile with: /clr  
#using <System.dll>  
#using <System.Drawing.dll>  
#using <System.Windows.Forms.dll>  
  
using namespace System;  
using namespace System::Windows::Forms;  
  
[STAThread] int main()  
{  
   String^ str = "This text is copied into the Clipboard.";  
  
   // Use 'true' as the second argument if  
   // the data is to remain in the clipboard  
   // after the program terminates.  
   Clipboard::SetDataObject(str, true);  
  
   Console::WriteLine("Added text to the Clipboard.");  
  
   return 0;  
}  
```  

## <a name="write_data"></a> Wpisywanie danych do rejestru Windows
Poniższy przykład kodu wykorzystuje <xref:Microsoft.Win32.Registry.CurrentUser> klawisz, aby utworzyć wystąpienie zapisywalny <xref:Microsoft.Win32.RegistryKey> klasy odpowiadający **oprogramowania** klucza. <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A> Metody jest następnie używany do tworzenia nowego klucza i Dodaj do par klucz/wartość.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// registry_write.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main()  
{  
   // The second OpenSubKey argument indicates that  
   // the subkey should be writable.   
   RegistryKey^ rk;  
   rk  = Registry::CurrentUser->OpenSubKey("Software", true);  
   if (!rk)  
   {  
      Console::WriteLine("Failed to open CurrentUser/Software key");  
      return -1;  
   }  
  
   RegistryKey^ nk = rk->CreateSubKey("NewRegKey");  
   if (!nk)  
   {  
      Console::WriteLine("Failed to create 'NewRegKey'");  
      return -1;  
   }  
  
   String^ newValue = "NewValue";  
   try  
   {  
      nk->SetValue("NewKey", newValue);  
      nk->SetValue("NewKey2", 44);  
   }  
   catch (Exception^)  
   {  
      Console::WriteLine("Failed to set new values in 'NewRegKey'");  
      return -1;  
   }  
  
   Console::WriteLine("New key created.");  
   Console::Write("Use REGEDIT.EXE to verify ");  
   Console::WriteLine("'CURRENTUSER/Software/NewRegKey'\n");  
   return 0;  
}  
```  
  
### <a name="remarks"></a>Uwagi  
 .NET Framework umożliwia dostęp do rejestru przy użyciu <xref:Microsoft.Win32.Registry> i [RegistryKey](https://msdn.microsoft.com/en-us/library/microsoft.win32.registrykey.aspx) klasy, które są zdefiniowane w <xref:Microsoft.Win32> przestrzeni nazw. **Rejestru** klasy jest kontenerem dla statycznych wystąpień <xref:Microsoft.Win32.RegistryKey> klasy. Każde wystąpienie reprezentuje węzeł główny rejestru. Wystąpienia są <xref:Microsoft.Win32.Registry.ClassesRoot>, <xref:Microsoft.Win32.Registry.CurrentConfig>, <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine>, i <xref:Microsoft.Win32.Registry.Users>.  

## <a name="related-sections"></a>Sekcje pokrewne  
 <xref:System.Environment>  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)

 [Wprowadzenie do monitorowania wydajności](http://msdn.microsoft.com/en-us/d40f10b9-e2b7-4ec8-a9b3-706929e5bf35) 