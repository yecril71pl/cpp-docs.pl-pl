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
ms.openlocfilehash: 99fce804ad30e01bdbaa99b1636a5238ff535f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371769"
---
# <a name="windows-operations-ccli"></a>Operacje związane z systemem Windows (C++/CLI)

Demonstruje różne zadania specyficzne dla systemu Windows przy użyciu sdk windows.

W poniższych tematach przedstawiono różne operacje systemu Windows wykonywane przy użyciu sdk systemu Windows przy użyciu języka Visual C++.

## <a name="determine-if-shutdown-has-started"></a><a name="determine_shutdown"></a>Określ, czy zamknięcie zostało rozpoczęte

Poniższy przykład kodu pokazuje, jak ustalić, czy aplikacja lub .NET Framework jest obecnie zakończone. Jest to przydatne do uzyskiwania dostępu do elementów statycznych w programie .NET Framework, ponieważ podczas zamykania systemu te konstrukcje są finalizowane przez system i nie mogą być niezawodnie używane. Sprawdzając <xref:System.Environment.HasShutdownStarted%2A> właściwość najpierw, można uniknąć potencjalnych awarii, nie uzyskując dostępu do tych elementów.

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

## <a name="determine-the-user-interactive-state"></a><a name="determine_user"></a>Określanie stanu interaktywnego użytkownika

Poniższy przykład kodu pokazuje, jak ustalić, czy kod jest uruchamiany w kontekście interakcyjnym użytkownika. Jeśli <xref:System.Environment.UserInteractive%2A> jest false, a następnie kod jest uruchomiony jako proces usługi lub od wewnątrz aplikacji sieci Web, w którym to przypadku nie należy podejmować próby interakcji z użytkownikiem.

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

## <a name="read-data-from-the-windows-registry"></a><a name="read_registry"></a>Odczytywanie danych z rejestru systemu Windows

Poniższy przykład kodu <xref:Microsoft.Win32.Registry.CurrentUser> używa klucza do odczytu danych z rejestru systemu Windows. Najpierw podkluczy są wyliczana <xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A> przy użyciu metody, a następnie <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> tożsamości podklucz jest otwierany przy użyciu metody. Podobnie jak klucze główne, każdy podklucz jest reprezentowany przez <xref:Microsoft.Win32.RegistryKey> klasę. Na koniec nowy <xref:Microsoft.Win32.RegistryKey> obiekt jest używany do wyliczenia par klucz/wartość.

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

Klasa <xref:Microsoft.Win32.Registry> jest tylko kontenerem dla statycznych <xref:Microsoft.Win32.RegistryKey>wystąpień . Każde wystąpienie reprezentuje węzeł rejestru głównego. Instancje <xref:Microsoft.Win32.Registry.ClassesRoot>to <xref:Microsoft.Win32.Registry.CurrentConfig> <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine>, <xref:Microsoft.Win32.Registry.Users>, i .

Oprócz statycznych obiektów w <xref:Microsoft.Win32.Registry> klasie są tylko do odczytu. Ponadto wystąpienia klasy, <xref:Microsoft.Win32.RegistryKey> które są tworzone w celu uzyskania dostępu do zawartości obiektów rejestru są tylko do odczytu, jak również. Aby uzyskać przykład zastępowania tego zachowania, zobacz [Jak: Zapisywanie danych w rejestrze systemu Windows (C++/CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md).

W klasie znajdują się <xref:Microsoft.Win32.Registry> dwa <xref:Microsoft.Win32.Registry.DynData> <xref:Microsoft.Win32.Registry.PerformanceData>dodatkowe obiekty: i . Oba są wystąpieniami <xref:Microsoft.Win32.RegistryKey> klasy. Obiekt <xref:Microsoft.Win32.Registry.DynData> zawiera dynamiczne informacje rejestru, który jest obsługiwany tylko w systemach Windows 98 i Windows Me. Obiekt <xref:Microsoft.Win32.Registry.PerformanceData> może służyć do uzyskiwania dostępu do informacji licznika wydajności dla aplikacji korzystających z systemu monitorowania wydajności systemu Windows. Węzeł <xref:Microsoft.Win32.Registry.PerformanceData> reprezentuje informacje, które nie są faktycznie przechowywane w rejestrze i dlatego nie można wyświetlać przy użyciu Regedit.exe.

## <a name="read-windows-performance-counters"></a><a name="read_performance"></a>Odczytywanie liczników wydajności systemu Windows

Niektóre aplikacje i podsystemy systemu Windows udostępniają dane dotyczące wydajności za pośrednictwem systemu wydajności systemu Windows. Liczniki te są dostępne <xref:System.Diagnostics.PerformanceCounterCategory> przy <xref:System.Diagnostics.PerformanceCounter> użyciu i klas, <xref:System.Diagnostics?displayProperty=fullName> które znajdują się w obszarze nazw.

Poniższy przykład kodu używa tych klas do pobierania i wyświetlania licznika, który jest aktualizowany przez system Windows, aby wskazać procent czasu, przez który procesor jest zajęty.

> [!NOTE]
> W tym przykładzie wymaga uprawnień administracyjnych do uruchomienia w systemie Windows Vista.

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

## <a name="retrieve-text-from-the-clipboard"></a><a name="retrieve_text"></a>Pobieranie tekstu ze Schowka

Poniższy przykład kodu <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> używa funkcji elementu członkowskiego, <xref:System.Windows.Forms.IDataObject> aby zwrócić wskaźnik do interfejsu. Ten interfejs można następnie zbadać dla formatu danych i używane do pobierania rzeczywistych danych.

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

## <a name="retrieve-the-current-username"></a><a name="retrieve_current"></a>Pobieranie bieżącej nazwy użytkownika

Poniższy przykład kodu pokazuje pobieranie bieżącej nazwy użytkownika (nazwa użytkownika zalogowanego do systemu Windows). Nazwa jest przechowywana <xref:System.Environment.UserName%2A> w ciągu, który <xref:System.Environment> jest zdefiniowany w obszarze nazw.

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

## <a name="retrieve-the-net-framework-version"></a><a name="retrieve_dotnet"></a>Pobieranie wersji programu .NET Framework

Poniższy przykład kodu pokazuje, jak określić wersję aktualnie zainstalowanego programu .NET Framework z <xref:System.Environment.Version%2A> właściwością, która jest wskaźnikiem do obiektu zawierającego <xref:System.Version> informacje o wersji.

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

## <a name="retrieve-the-local-machine-name"></a><a name="retrieve_local"></a>Pobieranie nazwy komputera lokalnego

Poniższy przykład kodu pokazuje pobieranie nazwy komputera lokalnego (nazwa komputera, jak pojawia się w sieci). Można to osiągnąć, <xref:System.Environment.MachineName%2A> uzyskując ciąg, który <xref:System.Environment> jest zdefiniowany w obszarze nazw.

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

## <a name="retrieve-the-windows-version"></a><a name="retrieve_version"></a>Pobieranie wersji systemu Windows

Poniższy przykład kodu pokazuje, jak pobrać informacje o platformie i wersji bieżącego systemu operacyjnego. Te informacje są <xref:System.Environment.OSVersion%2A?displayProperty=fullName> przechowywane we właściwości i składa się z wyliczenia, <xref:System.Environment.Version%2A> które opisuje wersję systemu Windows w ujęciu szerokim i obiekt, który zawiera dokładną kompilację systemu operacyjnego.

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

## <a name="retrieve-time-elapsed-since-startup"></a><a name="retrieve_time"></a>Pobieranie czasu, który upłynął od momentu uruchomienia

Poniższy przykład kodu pokazuje, jak określić liczbę znaczników lub liczbę milisekund, które upłynęły od momentu rozpoczęcia pracy systemu Windows. Ta wartość jest <xref:System.Environment.TickCount%2A?displayProperty=fullName> przechowywana w wemieć i, ponieważ jest to wartość 32-bitowa, resetuje się do zera co około 24,9 dni.

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

## <a name="store-text-in-the-clipboard"></a><a name="store_text"></a>Przechowywanie tekstu w Schowku

Poniższy przykład kodu <xref:System.Windows.Forms.Clipboard> używa obiektu <xref:System.Windows.Forms> zdefiniowanego w obszarze nazw do przechowywania ciągu. Ten obiekt udostępnia dwie <xref:System.Windows.Forms.Clipboard.SetDataObject%2A> <xref:System.Windows.Forms.Clipboard.GetDataObject%2A>funkcje członkowskie: i . Dane są przechowywane w Schowku, <xref:System.Object> wysyłając <xref:System.Windows.Forms.Clipboard.SetDataObject%2A>dowolny obiekt pochodzący z .

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

## <a name="write-data-to-the-windows-registry"></a><a name="write_data"></a>Zapisywanie danych w rejestrze systemu Windows

Poniższy przykład kodu <xref:Microsoft.Win32.Registry.CurrentUser> używa klucza do utworzenia <xref:Microsoft.Win32.RegistryKey> zapisywalne wystąpienie klasy odpowiadającej **klucza oprogramowania.** Metoda <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A> jest następnie używana do tworzenia nowego klucza i dodawania do par klucz/wartość.

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

Za pomocą programu .NET Framework można <xref:Microsoft.Win32.Registry> uzyskać <xref:Microsoft.Win32.RegistryKey> dostęp do rejestru z <xref:Microsoft.Win32> klasami i klasami, które są zdefiniowane w obszarze nazw. **Registry** Klasa jest kontenerem dla statycznych <xref:Microsoft.Win32.RegistryKey> wystąpień klasy. Każde wystąpienie reprezentuje węzeł rejestru głównego. Instancje <xref:Microsoft.Win32.Registry.ClassesRoot>to <xref:Microsoft.Win32.Registry.CurrentConfig> <xref:Microsoft.Win32.Registry.CurrentUser>, <xref:Microsoft.Win32.Registry.LocalMachine>, <xref:Microsoft.Win32.Registry.Users>, i .

## <a name="related-sections"></a>Sekcje pokrewne

<xref:System.Environment>

## <a name="see-also"></a>Zobacz też

[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
