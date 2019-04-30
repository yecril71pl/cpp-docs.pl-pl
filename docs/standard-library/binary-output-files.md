---
title: Binarne pliki wyjściowe
ms.date: 11/04/2016
helpviewer_keywords:
- I/O [C++], binary output files
- files [C++], binary output files
- binary data, binary output files
ms.assetid: 180954af-8cd6-444b-9a76-2f630a3389d8
ms.openlocfilehash: 99445275a8f92622f451e8a88082dc2b28fb60b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62414064"
---
# <a name="binary-output-files"></a>Binarne pliki wyjściowe

Strumienie pierwotnie zostały zaprojektowane dla tekstu, więc to domyślny tryb wyjściowy jest tekst. W trybie tekstowym znak nowego wiersza (szesnastkowa 10) rozszerza się na powrót karetki return-wysuwu wiersza (tylko 16-bitowy). Rozszerzenie może spowodować problemy, jak pokazano poniżej:

```cpp
// binary_output_files.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;
int iarray[2] = { 99, 10 };
int main( )
{
    ofstream os( "test.dat" );
    os.write( (char *) iarray, sizeof( iarray ) );
}
```

Można by oczekiwać na dane wyjściowe sekwencja bajtów {99, 0, 10, 0}; tego programu Zamiast tego Wyświetla {99, 0, 13, 10, 0}, która powoduje występowanie problemów, w programie oczekiwano binarnego danych wejściowych. Jeśli potrzebujesz true binarne dane wyjściowe, w którym zapisywane są znaki nieprzetłumaczone, można określić binarne dane wyjściowe przy użyciu [ofstream](../standard-library/basic-ofstream-class.md#basic_ofstream) argumentu openmode konstruktora:

```cpp
// binary_output_files2.cpp
// compile with: /EHsc
#include <fstream>
using namespace std;
int iarray[2] = { 99, 10 };

int main()
{
   ofstream ofs ( "test.dat", ios_base::binary );

   // Exactly 8 bytes written
   ofs.write( (char*)&iarray[0], sizeof(int)*2 );
}
```

## <a name="see-also"></a>Zobacz także

[Strumienie wyjściowe](../standard-library/output-streams.md)<br/>
