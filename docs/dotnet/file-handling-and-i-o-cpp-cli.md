---
title: Obsługa plików i we / wy (C + +/ CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- .NET Framework [C++], file handling
- files [C++], .NET Framework and
- I/O [C++], .NET Framework applications
- .NET Framework [C++], I/O
- files [C++], listing files
- directories [C++], listing files
- monitoring file system events
- FileSystemWatcher class, examples
- examples [C++], monitoring file system changes
- events [C++], monitoring
- file system events [C++]
- files [C++], binary
- binary files, reading in C++
- reading text files
- text files, reading
- files [C++], retrieving information about
- FileInfo class
- binary files, writing in C++
- files [C++], binary
- files [C++], text
- text files, writing in C++
ms.assetid: 3296fd59-a83a-40d4-bd4a-6096cc13101b
ms.openlocfilehash: 7009c0b017c403c3f0108aa84b8ddb25a1d1564f
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/11/2019
ms.locfileid: "57749376"
---
# <a name="file-handling-and-io-ccli"></a>Obsługa plików i we/wy (C++/CLI)

Demonstruje różne operacje na plikach za pomocą programu .NET Framework.

W poniższych tematach pokazano użycie klas zdefiniowanych w <xref:System.IO> przestrzeni nazw, aby wykonywać różne operacje na plikach.

## <a name="enumerate"></a> Wyliczanie plików w katalogu

Poniższy przykład kodu pokazuje, jak można pobrać listy plików w katalogu. Ponadto podkatalogi są wyliczane. Poniższy przykład kodu wykorzystuje <xref:System.IO.Directory.GetFiles%2A> <xref:System.IO.Directory.GetFiles%2A> i <xref:System.IO.Directory.GetDirectories%2A> metody, aby wyświetlić zawartość katalogu C:\Windows.

### <a name="example"></a>Przykład

```cpp
// enum_files.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;

int main()
{
   String^ folder = "C:\\";
   array<String^>^ dir = Directory::GetDirectories( folder );
   Console::WriteLine("--== Directories inside '{0}' ==--", folder);
   for (int i=0; i<dir->Length; i++)
      Console::WriteLine(dir[i]);

   array<String^>^ file = Directory::GetFiles( folder );
   Console::WriteLine("--== Files inside '{0}' ==--", folder);
   for (int i=0; i<file->Length; i++)
      Console::WriteLine(file[i]);

   return 0;
}
```

## <a name="monitor"></a> Monitorowanie zmian systemu plików

Poniższy przykład kodu wykorzystuje <xref:System.IO.FileSystemWatcher> do rejestrowania zdarzeń jest tworzone, zmienione, usunięty lub zmieniono nazwy plików. Zamiast okresowe sondowanie katalogu dla zmian w plikach, możesz użyć <xref:System.IO.FileSystemWatcher> klasy wyzwolenie zdarzenia po wykryciu zmiany.

### <a name="example"></a>Przykład

```cpp
// monitor_fs.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::IO;

ref class FSEventHandler
{
public:
    void OnChanged (Object^ source, FileSystemEventArgs^ e)
    {
        Console::WriteLine("File: {0} {1}",
               e->FullPath, e->ChangeType);
    }
    void OnRenamed(Object^ source, RenamedEventArgs^ e)
    {
        Console::WriteLine("File: {0} renamed to {1}",
                e->OldFullPath, e->FullPath);
    }
};

int main()
{
   array<String^>^ args = Environment::GetCommandLineArgs();

   if(args->Length < 2)
   {
      Console::WriteLine("Usage: Watcher.exe <directory>");
      return -1;
   }

   FileSystemWatcher^ fsWatcher = gcnew FileSystemWatcher( );
   fsWatcher->Path = args[1];
   fsWatcher->NotifyFilter = static_cast<NotifyFilters>
              (NotifyFilters::FileName |
               NotifyFilters::Attributes |
               NotifyFilters::LastAccess |
               NotifyFilters::LastWrite |
               NotifyFilters::Security |
               NotifyFilters::Size );

    FSEventHandler^ handler = gcnew FSEventHandler();
    fsWatcher->Changed += gcnew FileSystemEventHandler(
            handler, &FSEventHandler::OnChanged);
    fsWatcher->Created += gcnew FileSystemEventHandler(
            handler, &FSEventHandler::OnChanged);
    fsWatcher->Deleted += gcnew FileSystemEventHandler(
            handler, &FSEventHandler::OnChanged);
    fsWatcher->Renamed += gcnew RenamedEventHandler(
            handler, &FSEventHandler::OnRenamed);

    fsWatcher->EnableRaisingEvents = true;

    Console::WriteLine("Press Enter to quit the sample.");
    Console::ReadLine( );
}
```

## <a name="read_binary"></a> Odczytywanie pliku binarnego

Poniższy przykład kodu pokazuje, jak odczytywać dane binarne z pliku, przy użyciu dwóch klas z <xref:System.IO?displayProperty=fullName> przestrzeni nazw: <xref:System.IO.FileStream> i <xref:System.IO.BinaryReader>. <xref:System.IO.FileStream> reprezentuje rzeczywisty plik. <xref:System.IO.BinaryReader> udostępnia interfejs do strumienia, który zezwala na dostęp binarny.

Przykładowy kod odczytuje plik o nazwie data.bin i zawiera liczby całkowite w formacie binarnym. Aby uzyskać informacji na temat tego typu plików, zobacz [jak: Wpisywanie do pliku binarnego (C + +/ CLI)](../dotnet/how-to-write-a-binary-file-cpp-cli.md).

### <a name="example"></a>Przykład

```cpp
// binary_read.cpp
// compile with: /clr
#using<system.dll>
using namespace System;
using namespace System::IO;

int main()
{
   String^ fileName = "data.bin";
   try
   {
      FileStream^ fs = gcnew FileStream(fileName, FileMode::Open);
      BinaryReader^ br = gcnew BinaryReader(fs);

      Console::WriteLine("contents of {0}:", fileName);
      while (br->BaseStream->Position < br->BaseStream->Length)
         Console::WriteLine(br->ReadInt32().ToString());

      fs->Close( );
   }
   catch (Exception^ e)
   {
      if (dynamic_cast<FileNotFoundException^>(e))
         Console::WriteLine("File '{0}' not found", fileName);
      else
         Console::WriteLine("Exception: ({0})", e);
      return -1;
   }
   return 0;
}
```

## <a name="read_text"></a> Odczytywanie pliku tekstowego

Poniższy przykład kodu pokazuje, jak otworzyć i odczytać jeden wiersz pliku tekstowego w czasie, za pomocą <xref:System.IO.StreamReader> klasy, która jest zdefiniowana w <xref:System.IO?displayProperty=fullName> przestrzeni nazw. Wystąpienie tej klasy jest używany do otwierania pliku tekstowego i następnie <xref:System.IO.StreamReader.ReadLine%2A?displayProperty=fullName> metoda służy do pobierania każdego wiersza.

Ten przykładowy kod odczytuje plik o nazwie textfile.txt i zawiera tekst. Aby uzyskać informacji na temat tego typu plików, zobacz [jak: Wpisywanie tekstu do pliku tekstowego (C + +/ CLI)](../dotnet/how-to-write-a-text-file-cpp-cli.md).

### <a name="example"></a>Przykład

```cpp
// text_read.cpp
// compile with: /clr
#using<system.dll>
using namespace System;
using namespace System::IO;

int main()
{
   String^ fileName = "textfile.txt";
   try
   {
      Console::WriteLine("trying to open file {0}...", fileName);
      StreamReader^ din = File::OpenText(fileName);

      String^ str;
      int count = 0;
      while ((str = din->ReadLine()) != nullptr)
      {
         count++;
         Console::WriteLine("line {0}: {1}", count, str );
      }
   }
   catch (Exception^ e)
   {
      if (dynamic_cast<FileNotFoundException^>(e))
         Console::WriteLine("file '{0}' not found", fileName);
      else
         Console::WriteLine("problem reading file '{0}'", fileName);
   }

   return 0;
}
```

## <a name="retrieve"></a> Pobieranie informacji o pliku

Poniższy przykład kodu demonstruje <xref:System.IO.FileInfo> klasy. Jeśli nazwa pliku, można użyć tej klasy można pobrać informacji o pliku, np. rozmiar pliku, katalogu, imię i nazwisko oraz datę i godzinę utworzenia i ostatniej modyfikacji.

Ten kod pobiera informacje o plikach dla Notepad.exe.

### <a name="example"></a>Przykład

```cpp
// file_info.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;

int main()
{
   array<String^>^ args = Environment::GetCommandLineArgs();
   if (args->Length < 2)
   {
      Console::WriteLine("\nUSAGE : file_info <filename>\n\n");
      return -1;
   }

   FileInfo^ fi = gcnew FileInfo( args[1] );

   Console::WriteLine("file size: {0}", fi->Length );

   Console::Write("File creation date:  ");
   Console::Write(fi->CreationTime.Month.ToString());
   Console::Write(".{0}", fi->CreationTime.Day.ToString());
   Console::WriteLine(".{0}", fi->CreationTime.Year.ToString());

   Console::Write("Last access date:  ");
   Console::Write(fi->LastAccessTime.Month.ToString());
   Console::Write(".{0}", fi->LastAccessTime.Day.ToString());
   Console::WriteLine(".{0}", fi->LastAccessTime.Year.ToString());

   return 0;
}
```

## <a name="write_binary"></a> Wpisywanie do pliku binarnego

Poniższy przykład kodu pokazuje zapisu w pliku danych binarnych. Dwie klasy z <xref:System.IO> przestrzeni nazw są używane: <xref:System.IO.FileStream> i <xref:System.IO.BinaryWriter>. <xref:System.IO.FileStream> reprezentuje rzeczywisty plik podczas <xref:System.IO.BinaryWriter> zapewnia interfejs do strumienia, który zezwala na dostęp binarny.

Poniższy przykład kodu zapisuje plik zawierający liczb całkowitych w formacie binarnym. Ten plik można odczytać z kodu w [jak: Odczytywanie pliku binarnego (C + +/ CLI)](../dotnet/how-to-read-a-binary-file-cpp-cli.md).

### <a name="example"></a>Przykład

```cpp
// binary_write.cpp
// compile with: /clr
#using<system.dll>
using namespace System;
using namespace System::IO;

int main()
{
   array<Int32>^ data = {1, 2, 3, 10000};

   FileStream^ fs = gcnew FileStream("data.bin", FileMode::Create);
   BinaryWriter^ w = gcnew BinaryWriter(fs);

   try
   {
      Console::WriteLine("writing data to file:");
      for (int i=0; i<data->Length; i++)
      {
         Console::WriteLine(data[i]);
         w->Write(data[i]);
      }
   }
   catch (Exception^)
   {
     Console::WriteLine("data could not be written");
     fs->Close();
     return -1;
   }

   fs->Close();
   return 0;
}
```

## <a name="write_text"></a> Wpisywanie tekstu do pliku

Poniższy przykład kodu pokazuje, jak utworzyć plik tekstowy i wpisać tekst za pomocą <xref:System.IO.StreamWriter> klasy, która jest zdefiniowana w <xref:System.IO> przestrzeni nazw. <xref:System.IO.StreamWriter> Konstruktor przyjmuje nazwę pliku, który ma zostać utworzony. Jeśli plik istnieje, zostanie zastąpiony (chyba że przyjmie wartość True jako drugi <xref:System.IO.StringWriter> argumentu konstruktora).

Plik jest złożony za pomocą <xref:System.IO.StreamWriter.Write%2A> i <xref:System.IO.TextWriter.WriteLine%2A> funkcji.

### <a name="example"></a>Przykład

```cpp
// text_write.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;

int main()
{
   String^ fileName = "textfile.txt";

   StreamWriter^ sw = gcnew StreamWriter(fileName);
   sw->WriteLine("A text file is born!");
   sw->Write("You can use WriteLine");
   sw->WriteLine("...or just Write");
   sw->WriteLine("and do {0} output too.", "formatted");
   sw->WriteLine("You can also send non-text objects:");
   sw->WriteLine(DateTime::Now);
   sw->Close();
   Console::WriteLine("a new file ('{0}') has been written", fileName);

   return 0;
}
```

## <a name="see-also"></a>Zobacz także

[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[We/Wy plików i strumieni](/dotnet/standard/io/index)<br/>
[System.IO — przestrzeń nazw](/dotnet/api/system.io)
