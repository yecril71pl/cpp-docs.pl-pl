---
title: Wyrażenia regularne (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- regular expressions [C++]
- .NET Framework [C++], regular expressions
- regular expressions [C++], about regular expressions
- parsing strings [C++]
- examples [C++], strings
- regular expressions [C++], parsing strings
- Split method, parsing strings
- strings [C++], parsing
- substrings, simple matches
- searching, exact substring matches
- strings [C++], exact substring matching
- regular expressions [C++], simple matching
- IsMatch method
- strings [C++], extracting data from
- formatted strings [C++]
- regular expressions [C++], extracting data fields
- data [C++], extracting from strings
- regular expressions [C++], rearranging data
- data [C++], rearranging
- search and replace
- Replace method
- regular expressions [C++], search and replace
- strings [C++], formatting
- data [C++], formatting
- regular expressions [C++], validating data formatting
ms.assetid: 838bab49-0dbc-4089-a604-ef146269ef5a
ms.openlocfilehash: 24a278e4d5b208c5d8e3b95b9f5a0bd0306dbab3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384665"
---
# <a name="regular-expressions-ccli"></a>Wyrażenia regularne (C++/CLI)

Demonstruje różne operacje na ciągach przy użyciu klas wyrażeniach regularnych programu .NET Framework.

W poniższych tematach pokazano użycie programu .NET Framework <xref:System.Text.RegularExpressions> przestrzeni nazw (w jeden przypadek <xref:System.String.Split%2A?displayProperty=fullName> metody) do wyszukiwania, analizuje i zmodyfikować ciągi.

## <a name="parse_regex"></a> Analizowanie ciągów za pomocą wyrażeń regularnych

Poniższy przykład kodu demonstruje, prostego ciągu analizy przy użyciu <xref:System.Text.RegularExpressions.Regex> klasy w <xref:System.Text.RegularExpressions?displayProperty=fullName> przestrzeni nazw. Ciąg zawierający wiele typów ukośników word jest konstruowany. Ten ciąg jest analizowany przy użyciu <xref:System.Text.RegularExpressions.Regex> klasy w połączeniu z <xref:System.Text.RegularExpressions.Match> klasy. Następnie każdego wyrazu w zdaniu jest wyświetlany osobno.

### <a name="example"></a>Przykład

```cpp
// regex_parse.cpp
// compile with: /clr
#using <system.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main( )
{
   int words = 0;
   String^ pattern = "[a-zA-Z]*";
   Console::WriteLine( "pattern : '{0}'", pattern );
   Regex^ regex = gcnew Regex( pattern );

   String^ line = "one\ttwo three:four,five six  seven";
   Console::WriteLine( "text : '{0}'", line );
   for( Match^ match = regex->Match( line );
        match->Success; match = match->NextMatch( ) )
   {
      if( match->Value->Length > 0 )
      {
         words++;
         Console::WriteLine( "{0}", match->Value );
      }
   }
   Console::WriteLine( "Number of Words : {0}", words );

   return 0;
}
```

## <a name="parse_split"></a> Analizowanie ciągów za pomocą metody Split

Poniższy przykład kodu demonstruje sposób użycia <xref:System.String.Split%2A?displayProperty=fullName> metodę, aby wyodrębnić każdy wyraz z ciągu. Ciąg zawierający wiele typów ukośników word jest tworzony i następnie analizowane przez wywołanie metody <xref:System.String.Split%2A> z listą ukośników. Następnie każdego wyrazu w zdaniu jest wyświetlany osobno.

### <a name="example"></a>Przykład

```cpp
// regex_split.cpp
// compile with: /clr
using namespace System;

int main()
{
   String^ delimStr = " ,.:\t";
   Console::WriteLine( "delimiter : '{0}'", delimStr );
   array<Char>^ delimiter = delimStr->ToCharArray( );
   array<String^>^ words;
   String^ line = "one\ttwo three:four,five six seven";

   Console::WriteLine( "text : '{0}'", line );
   words = line->Split( delimiter );
   Console::WriteLine( "Number of Words : {0}", words->Length );
   for (int word=0; word<words->Length; word++)
      Console::WriteLine( "{0}", words[word] );

   return 0;
}
```

## <a name="regex_simple"></a> Używanie wyrażeń regularnych w przypadku prostego dopasowywania

Poniższy przykład kodu używa wyrażeń regularnych do wyszukiwania podciągu dokładnego dopasowania. Wyszukiwanie jest wykonywane przez statyczną <xref:System.Text.RegularExpressions.Regex.IsMatch%2A> metody, która przyjmuje dwa ciągi jako dane wejściowe. Pierwsza to ciąg do wyszukania, a drugi jest wzorzec, które mają być wyszukiwane.

### <a name="example"></a>Przykład

```cpp
// regex_simple.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main()
{
   array<String^>^ sentence =
   {
      "cow over the moon",
      "Betsy the Cow",
      "cowering in the corner",
      "no match here"
   };

   String^ matchStr = "cow";
   for (int i=0; i<sentence->Length; i++)
   {
      Console::Write( "{0,24}", sentence[i] );
      if ( Regex::IsMatch( sentence[i], matchStr,
                     RegexOptions::IgnoreCase ) )
         Console::WriteLine("  (match for '{0}' found)", matchStr);
      else
         Console::WriteLine("");
   }
   return 0;
}
```

## <a name="regex_extract"></a> Używanie wyrażeń regularnych do wyodrębniania pól danych

Poniższy przykład kodu demonstruje użycie wyrażeń regularnych do wyodrębniania danych z ciąg formatowania. Poniższy przykład kodu wykorzystuje <xref:System.Text.RegularExpressions.Regex> klasy do określania wzorca, który odnosi się do adresu e-mail. Ten wzorzec zawiera identyfikatory pola, które może służyć do pobierania użytkownika i nazwę hosta części każdego z adresów e-mail. <xref:System.Text.RegularExpressions.Match> Klasa jest używana do wykonania dopasowania wzorca rzeczywistych. Jeśli adres e-mail danego jest prawidłowy, nazwę użytkownika i nazwy hostów są wyodrębniane i wyświetlane.

### <a name="example"></a>Przykład

```cpp
// Regex_extract.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace System::Text::RegularExpressions;

int main()
{
    array<String^>^ address=
    {
        "jay@southridgevideo.com",
        "barry@adatum.com",
        "treyresearch.net",
        "karen@proseware.com"
    };

    Regex^ emailregex = gcnew Regex("(?<user>[^@]+)@(?<host>.+)");

    for (int i=0; i<address->Length; i++)
    {
        Match^ m = emailregex->Match( address[i] );
        Console::Write("\n{0,25}", address[i]);

        if ( m->Success )
        {
            Console::Write("   User='{0}'",
            m->Groups["user"]->Value);
            Console::Write("   Host='{0}'",
            m->Groups["host"]->Value);
        }
        else
            Console::Write("   (invalid email address)");
        }

    Console::WriteLine("");
    return 0;
}
```

## <a name="regex_rearrange"></a> Używanie wyrażeń regularnych do zmiany rozmieszczenia danych

Poniższy przykład kodu pokazuje, jak obsługa wyrażeń regularnych programu .NET Framework można ponownie rozmieścić, lub ponownie sformatuj dane. Poniższy przykład kodu wykorzystuje <xref:System.Text.RegularExpressions.Regex> i <xref:System.Text.RegularExpressions.Match> klasy, aby wyodrębnić imiona i nazwiska z ciągu, a następnie wyświetlić te elementy nazwy w odwrotnej kolejności.

<xref:System.Text.RegularExpressions.Regex> Klasa jest używana do konstruowania wyrażenia regularnego, który opisuje bieżący format danych. Obie nazwy przyjmuje, że są oddzielone przecinkami i przy użyciu dowolnej ilości odstęp wokół przecinek. <xref:System.Text.RegularExpressions.Match> Metody jest następnie używany do analizowania każdego ciągu. Jeśli to się powiedzie, imienia i nazwiska są pobierane z <xref:System.Text.RegularExpressions.Match> obiektu i wyświetlane.

### <a name="example"></a>Przykład

```cpp
// regex_reorder.cpp
// compile with: /clr
#using <System.dll>
using namespace System;
using namespace Text::RegularExpressions;

int main()
{
   array<String^>^ name =
   {
      "Abolrous, Sam",
      "Berg,Matt",
      "Berry , Jo",
      "www.contoso.com"
   };

   Regex^ reg = gcnew Regex("(?<last>\\w*)\\s*,\\s*(?<first>\\w*)");

   for ( int i=0; i < name->Length; i++ )
   {
      Console::Write( "{0,-20}", name[i] );
      Match^ m = reg->Match( name[i] );
      if ( m->Success )
      {
         String^ first = m->Groups["first"]->Value;
         String^ last = m->Groups["last"]->Value;
         Console::WriteLine("{0} {1}", first, last);
      }
      else
         Console::WriteLine("(invalid)");
   }
   return 0;
}
```

## <a name="regex_search"></a> Używanie wyrażeń regularnych do wyszukiwania i zamieniania

Poniższy przykład kodu demonstruje sposób klasy wyrażeń regularnych <xref:System.Text.RegularExpressions.Regex> może służyć do wykonywania wyszukiwania i zamieniania. Jest to zrobić za pomocą <xref:System.Text.RegularExpressions.Regex.Replace%2A> metody. Wersja użyta przyjmuje dwa ciągi jako dane wejściowe: ciąg, który ma zostać zmodyfikowana, a ciąg, który ma zostać wstawiony zamiast sekcje (jeśli istnieje) który pasuje do wzorca, umożliwiającej <xref:System.Text.RegularExpressions.Regex> obiektu.

Ten kod zastępuje wszystkie cyfry w ciągu znaków podkreślenia (_), a następnie zastępuje z pustym ciągiem, powodując rzeczywiste usunięcie ich. Ten sam efekt można osiągnąć w jednym kroku, ale w tym miejscu służą dwa kroki dla celów demonstracyjnych.

### <a name="example"></a>Przykład

```cpp
// regex_replace.cpp
// compile with: /clr
#using <System.dll>
using namespace System::Text::RegularExpressions;
using namespace System;

int main()
{
   String^ before = "The q43uick bro254wn f0ox ju4mped";
   Console::WriteLine("original  : {0}", before);

   Regex^ digitRegex = gcnew Regex("(?<digit>[0-9])");
   String^ after = digitRegex->Replace(before, "_");
   Console::WriteLine("1st regex : {0}", after);

   Regex^ underbarRegex = gcnew Regex("_");
   String^ after2 = underbarRegex->Replace(after, "");
   Console::WriteLine("2nd regex : {0}", after2);

   return 0;
}
```

## <a name="regex_validate"></a> Używanie wyrażeń regularnych do walidacji formatowania danych

Poniższy przykład kodu demonstruje użycie wyrażenia regularne, aby sprawdzić formatowanie ciągu. W poniższym przykładzie kodu powinien on zawierać prawidłowy numer telefonu. Poniższy przykład kodu używa ciągu "\d{3}-\d{3}-\d{4}" Aby wskazać, że każde pole reprezentuje prawidłowy numer telefonu. W ciągu "d" oznacza cyfrę, a argument po każdym "d" wskazuje liczbę cyfr, które muszą być obecne. W tym przypadku numer będzie musiał być oddzielone kreskami.

### <a name="example"></a>Przykład

```cpp
// regex_validate.cpp
// compile with: /clr
#using <System.dll>

using namespace System;
using namespace Text::RegularExpressions;

int main()
{
   array<String^>^ number =
   {
      "123-456-7890",
      "444-234-22450",
      "690-203-6578",
      "146-893-232",
      "146-839-2322",
      "4007-295-1111",
      "407-295-1111",
      "407-2-5555",
   };

   String^ regStr = "^\\d{3}-\\d{3}-\\d{4}$";

   for ( int i = 0; i < number->Length; i++ )
   {
      Console::Write( "{0,14}", number[i] );

      if ( Regex::IsMatch( number[i], regStr ) )
         Console::WriteLine(" - valid");
      else
         Console::WriteLine(" - invalid");
   }
   return 0;
}
```

## <a name="related-sections"></a>Sekcje pokrewne

[Wyrażeń regularnych programu .NET framework](/dotnet/standard/base-types/regular-expressions)

## <a name="see-also"></a>Zobacz także

[Programowanie .NET w języku C++/interfejsie wiersza polecenia (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
