---
title: Inne manipulatory strumieni wyjściowych z jednym argumentem
ms.date: 11/04/2016
helpviewer_keywords:
- output streams, one-argument manipulators
ms.assetid: e381dee8-6b16-4cef-805a-4a6a1d2b696b
ms.openlocfilehash: 8fe30a0df70d84f7a8a9eafcdf22439cbe321043
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224646"
---
# <a name="other-one-argument-output-stream-manipulators"></a>Inne manipulatory strumieni wyjściowych z jednym argumentem

Poniższy przykład używa klasy `money` , która jest **`long`** typem. `setpic`Manipulator dołącza ciąg "Picture" formatowania do klasy, która może być używana przez operator wstawiania przeciążonego strumienia klasy `money` . Ciąg obrazu jest przechowywany jako zmienna statyczna w `money` klasie, a nie jako element członkowski danych klasy strumienia, więc nie trzeba tworzyć nowej klasy strumienia wyjściowego.

## <a name="example"></a>Przykład

```cpp
// one_arg_output.cpp
// compile with: /GR /EHsc
#include <iostream>
#include <iomanip>
#include <string>
using namespace std;

typedef char* charp;

class money
{
private:
    long value;
    static char *szCurrentPic;
public:
    money( long val ) { value = val; }
    friend ostream& operator << ( ostream& os, money m ) {
        // A more complete function would merge the picture
        // with the value rather than simply appending it
        os << m.value << '[' << money::szCurrentPic << ']';
        return os;
    }
    static void setpic( char* szPic ) {
        money::szCurrentPic = new char[strlen( szPic ) + 1];
        strcpy_s( money::szCurrentPic, strlen( szPic ) + 1, szPic );
    }
};

char *money::szCurrentPic;  // Static pointer to picture

void fb( ios_base& os, char * somename )
{
   money::setpic(somename);
/*
   ostream *pos = dynamic_cast<ostream*>(&os);
   if (pos)
   {
      for( int i=0; i < l; i++ )
      (*pos) << ' ';
   };
*/
}

_Smanip<charp>
   __cdecl setpic(char * somename)
   {
   return (_Smanip<charp>(&fb, somename));
   }

int main( )
{
    money amt = (long)35235.22;
    cout << setiosflags( ios::fixed );
    cout << setpic( "###,###,###.##" ) << "amount = " << amt << endl;
}
```

## <a name="see-also"></a>Zobacz także

[Niestandardowe manipulowanie z argumentami](../standard-library/custom-manipulators-with-arguments.md)
