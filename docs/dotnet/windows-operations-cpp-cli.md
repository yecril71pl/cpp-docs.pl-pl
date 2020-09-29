---
title: Operacje związane z systemem Windows (C++/CLI)
ms.date: 11/04/2016
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
ms.openlocfilehash: 3c4ef2a69c25313ff444e0fabaea6eef2feeeee2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501657"
---
# <a name="windows-operations-ccli"></a>Operacje związane z systemem Windows (C++/CLI)

Demonstruje różne zadania specyficzne dla systemu Windows przy użyciu Windows SDK.

W poniższych tematach przedstawiono różne operacje systemu Windows wykonywane z Windows SDK przy użyciu Visual C++.

## <a name="determine-if-shutdown-has-started"></a><a name="determine_shutdown"></a> Ustalanie, czy zamykanie zostało rozpoczęte

Poniższy przykład kodu demonstruje, jak ustalić, czy aplikacja lub .NET Framework są obecnie przerywane. Jest to przydatne do uzyskiwania dostępu do elementów statycznych w .NET Framework, ponieważ podczas zamykania te konstrukcje są finalizowane przez system i nie można ich w sposób wiarygodny wykorzystać. Sprawdzając <xref:System.Environment.HasShutdownStarted%2A> najpierw właściwość, można uniknąć potencjalnych błędów, nie uzyskując dostępu do tych elementów.

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

## <a name="determine-the-user-interactive-state"></a><a name="determine_user"></a> Określ stan interaktywny użytkownika

Poniższy przykład kodu demonstruje, jak ustalić, czy kod jest uruchamiany w kontekście użytkownika interakcyjnego. Jeśli <xref:System.Environment.UserInteractive%2A> ma wartość false, kod działa jako proces usługi lub wewnątrz aplikacji sieci Web, w tym przypadku nie należy próbować korzystać z tego użytkownika.

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

## <a name="read-data-from-the-windows-registry"></a><a name="read_registry"></a> Odczytywanie danych z rejestru systemu Windows

Poniższy przykład kodu używa <xref:Microsoft.Win32.Registry.CurrentUser> klucza do odczytywania danych z rejestru systemu Windows. Najpierw podklucze są wyliczane przy użyciu <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> metody, a następnie podklucz tożsamości jest otwierany przy użyciu <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> metody. Podobnie jak klucze główne, każdy podklucz jest reprezentowany przez <xref:Microsoft.Win32.RegistryKey> klasę. Na koniec nowy <xref:Microsoft.Win32.RegistryKey> obiekt jest używany do wyliczania par klucz/wartość.

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

<xref:Microsoft.Win32.Registry>Klasa jest tylko kontenerem dla wystąpień statycznych <xref:Microsoft.Win32.RegistryKey> . Każde wystąpienie reprezentuje węzeł głównego rejestru. Wystąpieniami są <xref:Microsoft.Win32.Registry.ClassesRoot> , <xref:Microsoft.Win32.Registry.CurrentConfig> , <xref:Microsoft.Win32.Registry.CurrentUser> , <xref:Microsoft.Win32.Registry.LocalMachine> i <xref:Microsoft.Win32.Registry.Users> .

Oprócz statycznego obiekty w <xref:Microsoft.Win32.Registry> klasie są tylko do odczytu. Ponadto wystąpienia <xref:Microsoft.Win32.RegistryKey> klasy, które są tworzone w celu uzyskania dostępu do zawartości obiektów rejestru są również tylko do odczytu. Aby zapoznać się z przykładem sposobu przesłonięcia tego zachowania, zobacz [How to: Write Data in the Windows Registry (C++/CLI)](#write_data).

Istnieją dwa dodatkowe obiekty w <xref:Microsoft.Win32.Registry> klasie: <xref:Microsoft.Win32.Registry.DynData> i <xref:Microsoft.Win32.Registry.PerformanceData> . Oba są wystąpieniami <xref:Microsoft.Win32.RegistryKey> klasy. <xref:Microsoft.Win32.Registry.DynData>Obiekt zawiera informacje rejestru dynamicznego, które są obsługiwane tylko w systemach windows 98 i Windows Me. <xref:Microsoft.Win32.Registry.PerformanceData>Obiekt może służyć do uzyskiwania dostępu do informacji o liczniku wydajności dla aplikacji korzystających z systemu monitorowania wydajności systemu Windows. <xref:Microsoft.Win32.Registry.PerformanceData>Węzeł reprezentuje informacje, które nie są przechowywane w rejestrze i w związku z tym nie można ich przeglądać przy użyciu Regedit.exe.

## <a name="read-windows-performance-counters"></a><a name="read_performance"></a> Odczytywanie liczników wydajności systemu Windows

Niektóre aplikacje i podsystemy systemu Windows uwidaczniają dane wydajności za pomocą systemu wydajności systemu Windows. Dostęp do tych liczników można uzyskać przy <xref:System.Diagnostics.PerformanceCounterCategory> użyciu <xref:System.Diagnostics.PerformanceCounter> klas i, które znajdują się w <xref:System.Diagnostics?displayProperty=fullName> przestrzeni nazw.

Poniższy przykład kodu używa tych klas do pobierania i wyświetlania licznika, który jest aktualizowany przez system Windows, aby wskazać procent czasu, w którym procesor jest zajęty.

> [!NOTE]
> Ten przykład wymaga uprawnień administracyjnych do uruchomienia w systemie Windows Vista.

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

## <a name="retrieve-text-from-the-clipboard"></a><a name="retrieve_text"></a> Pobierz tekst ze schowka

Poniższy przykład kodu używa <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> funkcji elementu członkowskiego, aby zwrócić wskaźnik do <xref:System.Windows.Forms.IDataObject> interfejsu. Następnie można wykonać zapytanie dotyczące formatu danych i użyć ich do pobrania rzeczywistych danych.

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

## <a name="retrieve-the-current-username"></a><a name="retrieve_current"></a> Pobierz bieżącą nazwę użytkownika

Poniższy przykład kodu demonstruje pobieranie bieżącej nazwy użytkownika (nazwa użytkownika zalogowanego w systemie Windows). Nazwa jest przechowywana w <xref:System.Environment.UserName%2A> ciągu, który jest zdefiniowany w <xref:System.Environment> przestrzeni nazw.

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

## <a name="retrieve-the-net-framework-version"></a><a name="retrieve_dotnet"></a> Pobierz wersję .NET Framework

Poniższy przykład kodu demonstruje, jak określić wersję aktualnie zainstalowanej .NET Framework z <xref:System.Environment.Version%2A> właściwością, która jest wskaźnikiem do <xref:System.Version> obiektu, który zawiera informacje o wersji.

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

## <a name="retrieve-the-local-machine-name"></a><a name="retrieve_local"></a> Pobieranie nazwy komputera lokalnego

Poniższy przykład kodu demonstruje pobieranie nazwy komputera lokalnego (nazwa komputera wyświetlanego w sieci). Można to osiągnąć przez pobranie <xref:System.Environment.MachineName%2A> ciągu, który jest zdefiniowany w <xref:System.Environment> przestrzeni nazw.

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

## <a name="retrieve-the-windows-version"></a><a name="retrieve_version"></a> Pobierz wersję systemu Windows

Poniższy przykład kodu demonstruje sposób pobierania informacji o platformie i wersji bieżącego systemu operacyjnego. Te informacje są przechowywane we <xref:System.Environment.OSVersion%2A?displayProperty=fullName> właściwości i składają się na Wyliczenie opisujące wersję systemu Windows w szerszym zakresie oraz <xref:System.Environment.Version%2A> obiekt, który zawiera dokładną kompilację systemu operacyjnego.

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

## <a name="retrieve-time-elapsed-since-startup"></a><a name="retrieve_time"></a> Pobierz czas, który upłynął od uruchomienia

Poniższy przykład kodu demonstruje, jak określić liczbę cykli lub liczbę milisekund, które upłynęły od momentu uruchomienia systemu Windows. Ta wartość jest przechowywana w <xref:System.Environment.TickCount%2A?displayProperty=fullName> elemencie członkowskim i, ponieważ jest wartością 32-bitową, jest resetowana do zera w przybliżeniu co 24,9 dni.

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

## <a name="store-text-in-the-clipboard"></a><a name="store_text"></a> Przechowywanie tekstu w schowku

Poniższy przykład kodu używa <xref:System.Windows.Forms.Clipboard> obiektu zdefiniowanego w <xref:System.Windows.Forms> przestrzeni nazw do przechowywania ciągu. Ten obiekt zawiera dwie funkcje Członkowskie: <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> i <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> . Dane są przechowywane w schowku przez wysłanie wszelkich obiektów pochodnych z <xref:System.Object> do <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> .

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

## <a name="write-data-to-the-windows-registry"></a><a name="write_data"></a> Zapisz dane w rejestrze systemu Windows

Poniższy przykład kodu używa <xref:Microsoft.Win32.Registry.CurrentUser> klucza w celu utworzenia wystąpienia klasy z możliwością zapisu <xref:Microsoft.Win32.RegistryKey> odpowiadającego kluczowi **oprogramowania** . <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>Metoda jest następnie używana do tworzenia nowego klucza i dodawania do par klucz/wartość.

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

Za pomocą .NET Framework można uzyskać dostęp do rejestru przy użyciu <xref:Microsoft.Win32.Registry> klas i <xref:Microsoft.Win32.RegistryKey> , które są zdefiniowane w <xref:Microsoft.Win32> przestrzeni nazw. Klasa **rejestru** jest kontenerem dla wystąpień statycznych <xref:Microsoft.Win32.RegistryKey> klasy. Każde wystąpienie reprezentuje węzeł głównego rejestru. Wystąpieniami są <xref:Microsoft.Win32.Registry.ClassesRoot> , <xref:Microsoft.Win32.Registry.CurrentConfig> , <xref:Microsoft.Win32.Registry.CurrentUser> , <xref:Microsoft.Win32.Registry.LocalMachine> i <xref:Microsoft.Win32.Registry.Users> .

## <a name="related-sections"></a>Sekcje pokrewne

<xref:System.Environment>

## <a name="see-also"></a>Zobacz też

[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
