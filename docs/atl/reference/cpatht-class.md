---
title: Klasa CPathT | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CPathT
- ATLPATH/ATL::CPathT
- ATLPATH/ATL::CPathT::PCXSTR
- ATLPATH/ATL::CPathT::PXSTR
- ATLPATH/ATL::CPathT::XCHAR
- ATLPATH/ATL::CPathT::CPathT
- ATLPATH/ATL::CPathT::AddBackslash
- ATLPATH/ATL::CPathT::AddExtension
- ATLPATH/ATL::CPathT::Append
- ATLPATH/ATL::CPathT::BuildRoot
- ATLPATH/ATL::CPathT::Canonicalize
- ATLPATH/ATL::CPathT::Combine
- ATLPATH/ATL::CPathT::CommonPrefix
- ATLPATH/ATL::CPathT::CompactPath
- ATLPATH/ATL::CPathT::CompactPathEx
- ATLPATH/ATL::CPathT::FileExists
- ATLPATH/ATL::CPathT::FindExtension
- ATLPATH/ATL::CPathT::FindFileName
- ATLPATH/ATL::CPathT::GetDriveNumber
- ATLPATH/ATL::CPathT::GetExtension
- ATLPATH/ATL::CPathT::IsDirectory
- ATLPATH/ATL::CPathT::IsFileSpec
- ATLPATH/ATL::CPathT::IsPrefix
- ATLPATH/ATL::CPathT::IsRelative
- ATLPATH/ATL::CPathT::IsRoot
- ATLPATH/ATL::CPathT::IsSameRoot
- ATLPATH/ATL::CPathT::IsUNC
- ATLPATH/ATL::CPathT::IsUNCServer
- ATLPATH/ATL::CPathT::IsUNCServerShare
- ATLPATH/ATL::CPathT::MakePretty
- ATLPATH/ATL::CPathT::MatchSpec
- ATLPATH/ATL::CPathT::QuoteSpaces
- ATLPATH/ATL::CPathT::RelativePathTo
- ATLPATH/ATL::CPathT::RemoveArgs
- ATLPATH/ATL::CPathT::RemoveBackslash
- ATLPATH/ATL::CPathT::RemoveBlanks
- ATLPATH/ATL::CPathT::RemoveExtension
- ATLPATH/ATL::CPathT::RemoveFileSpec
- ATLPATH/ATL::CPathT::RenameExtension
- ATLPATH/ATL::CPathT::SkipRoot
- ATLPATH/ATL::CPathT::StripPath
- ATLPATH/ATL::CPathT::StripToRoot
- ATLPATH/ATL::CPathT::UnquoteSpaces
- ATLPATH/ATL::CPathT::m_strPath
dev_langs:
- C++
helpviewer_keywords:
- CPathT class
ms.assetid: eba4137d-1fd2-4b44-a2e1-0944db64df3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60541891832a3d466f7396086ac0918108991582
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43753165"
---
# <a name="cpatht-class"></a>Klasa CPathT

Ta klasa reprezentuje ścieżkę.

> [!IMPORTANT]
>  Ta klasa i jej elementów członkowskich nie można użyć w aplikacjach korzystających ze środowiska wykonawczego Windows.

## <a name="syntax"></a>Składnia

```
template <typename StringType>
class CPathT
```

#### <a name="parameters"></a>Parametry

*StringType*  
Klasa string ATL i MFC do użycia dla ścieżki (zobacz [CStringT](../../atl-mfc-shared/reference/cstringt-class.md)).

## <a name="members"></a>Elementy członkowskie

### <a name="public-typedefs"></a>Publiczne definicje typów

|Nazwa|Opis|
|----------|-----------------|
|[CPathT::PCXSTR](#pcxstr)|Typ stałym ciągiem.|
|[CPathT::PXSTR](#pxstr)|Typ ciągu.|
|[CPathT::XCHAR](#xchar)|Typ znaku.|

### <a name="public-constructors"></a>Konstruktory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPathT::CPathT](#cpatht)|Konstruktor dla ścieżki.|

### <a name="public-methods"></a>Metody publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPathT::AddBackslash](#addbackslash)|Wywołaj tę metodę, aby dodać ukośnik odwrotny na końcu ciągu, aby utworzyć poprawną składnię dla ścieżki.|
|[CPathT::AddExtension](#addextension)|Wywołaj tę metodę, aby dodać rozszerzenie pliku do ścieżki.|
|[CPathT::Append](#append)|Wywołaj tę metodę, aby dołączyć ciąg w bieżącej ścieżce.|
|[CPathT::BuildRoot](#buildroot)|Wywołaj tę metodę, aby utworzyć ścieżkę katalogu głównego z liczbą danego dysku.|
|[CPathT::Canonicalize](#canonicalize)|Wywołaj tę metodę, aby przekonwertować ścieżkę do postaci kanonicznej.|
|[CPathT::Combine](#combine)|Wywołaj tę metodę, aby złączyć ciąg reprezentujący nazwę katalogu i ciąg reprezentujący nazwę ścieżki pliku w jednej ścieżki.|
|[CPathT::CommonPrefix](#commonprefix)|Wywołaj tę metodę w celu określenia, czy podana ścieżka udostępni Wspólny prefiks bieżącej ścieżce.|
|[CPathT::CompactPath](#compactpath)|Wywołaj tę metodę, aby obciąć ścieżki pliku w celu dopasowania szerokość piksela podanego przez zamianę składników ścieżki elipsy.|
|[CPathT::CompactPathEx](#compactpathex)|Wywołaj tę metodę, aby obciąć mieścić się w danej liczby znaków, zastępując składników ścieżki wielokropek ścieżki pliku.|
|[CPathT::FileExists](#fileexists)|Wywołaj tę metodę, aby sprawdzić, czy istnieje plik o tej nazwie ścieżki.|
|[CPathT::FindExtension](#findextension)|Wywołaj tę metodę, aby znaleźć położenie rozszerzenie pliku w ścieżce.|
|[CPathT::FindFileName](#findfilename)|Wywołaj tę metodę, aby znaleźć położenie nazwę pliku w ścieżce.|
|[CPathT::GetDriveNumber](#getdrivenumber)|Wywołaj tę metodę, aby wyszukać ścieżkę do litery dysku w zakresie od "A" do "Z" i zwróć odpowiedni numer dysku.|
|[CPathT::GetExtension](#getextension)|Wywołaj tę metodę, aby pobrać rozszerzenie pliku ze ścieżki.|
|[CPathT::IsDirectory](#isdirectory)|Wywołaj tę metodę, aby sprawdzić, czy ścieżka jest prawidłowy katalog.|
|[CPathT::IsFileSpec](#isfilespec)|Wywołanie tej metody, aby wyszukać ścieżkę znaków rozdzielający ścieżki (na przykład, ":" lub "\\"). W przypadku żadne rozdzielający ścieżki znaki nie istnieje ścieżka uważany jest za ścieżką specyfikacji pliku.|
|[CPathT::IsPrefix](#isprefix)|Wywołaj tę metodę, aby określić, czy ścieżka zawiera prawidłowy prefiks przekazany typ *pszPrefix*.|
|[CPathT::IsRelative](#isrelative)|Wywołaj tę metodę w celu ustalenia, czy ścieżka jest względna.|
|[CPathT::IsRoot](#isroot)|Wywołaj tę metodę w celu określenia, czy ścieżka katalogu głównego.|
|[CPathT::IsSameRoot](#issameroot)|Wywołaj tę metodę, aby określić, czy inną ścieżkę ma typowe składnik główny przy użyciu bieżącej ścieżki.|
|[CPathT::IsUNC](#isunc)|Wywołaj tę metodę w celu ustalenia, czy ścieżka jest prawidłową ścieżkę UNC (universal Konwencja nazewnictwa) dla serwera i udostępniania.|
|[CPathT::IsUNCServer](#isuncserver)|Wywołaj tę metodę, aby określić, czy ścieżka jest prawidłową ścieżkę UNC (universal Konwencja nazewnictwa) tylko w przypadku serwera.|
|[CPathT::IsUNCServerShare](#isuncservershare)|Wywołaj tę metodę w celu określenia, czy ścieżka jest prawidłowa ścieżka UNC (universal Konwencja nazewnictwa) udziału, \\ \  *serwera*\ *udostępnianie*.|
|[CPathT::MakePretty](#makepretty)|Wywołaj tę metodę, aby przekonwertować ścieżkę, aby wszystkie małe litery, aby zapewnić spójny wygląd ścieżki.|
|[CPathT::MatchSpec](#matchspec)|Wywołaj tę metodę, aby wyszukać ścieżkę dla ciąg zawierający typ dopasowania symboli wieloznacznych.|
|[CPathT::QuoteSpaces](#quotespaces)|Wywołaj tę metodę, aby ująć w znaki cudzysłowu ścieżkę, jeśli zawiera on żadnych spacji.|
|[CPathT::RelativePathTo](#relativepathto)|Wywołaj tę metodę, aby utworzyć ścieżkę względną z jednego pliku lub folderu.|
|[CPathT::RemoveArgs](#removeargs)|Wywołaj tę metodę w celu usunięcia żadnych argumentów wiersza polecenia przy użyciu ścieżki.|
|[CPathT::RemoveBackslash](#removebackslash)|Wywołaj tę metodę, aby usunąć ukośnik odwrotny na końcu ze ścieżki.|
|[CPathT::RemoveBlanks](#removeblanks)|Wywołaj tę metodę w celu usunięcia wszystkich spacji wiodących i końcowych przy użyciu ścieżki.|
|[CPathT::RemoveExtension](#removeextension)|Wywołaj tę metodę, aby usunąć rozszerzenie pliku ze ścieżki, jeśli taka istnieje.|
|[CPathT::RemoveFileSpec](#removefilespec)|Wywołaj tę metodę, aby usunąć końcowe nazwę pliku i kreski ułamkowej odwróconej ze ścieżki, jeśli je ma.|
|[CPathT::RenameExtension](#renameextension)|Wywołaj tę metodę, aby zastąpić nowego rozszerzenia rozszerzenie nazwy pliku w ścieżce. Jeśli nazwa pliku zawiera rozszerzenie, rozszerzenie zostanie dołączony do końca ciągu.|
|[CPathT::SkipRoot](#skiproot)|Wywołaj tę metodę można przeanalizować ścieżki, ignorowanie literę dysku i części ścieżki serwera/udział UNC.|
|[CPathT::StripPath](#strippath)|Wywołaj tę metodę, aby usunąć część ścieżki pełną ścieżkę i nazwę pliku.|
|[CPathT::StripToRoot](#striptoroot)|Wywołaj tę metodę, aby usunąć wszystkie części ścieżki, z wyjątkiem informacji katalogu głównego.|
|[CPathT::UnquoteSpaces](#unquotespaces)|Wywołaj tę metodę, aby usunąć znaki cudzysłowu na początku i końca ścieżki.|

### <a name="public-operators"></a>Operatory publiczne

|Nazwa|Opis|
|----------|-----------------|
|[CPathT::operator const StringType &](#operator_const_stringtype_amp)|Ten operator sprawia, że obiekt traktowane jak ciąg.|
|[CPathT::operator CPathT::PCXSTR](#operator_cpatht__pcxstr)|Ten operator sprawia, że obiekt traktowane jak ciąg.|
|[CPathT::operator StringType &](#operator_stringtype)|Ten operator sprawia, że obiekt traktowane jak ciąg.|
|[CPathT::operator +=](#operator_add_eq)|Ten operator dołącza ciąg do ścieżki.|

### <a name="public-data-members"></a>Publiczne elementy członkowskie danych

|Nazwa|Opis|
|----------|-----------------|
|[CPathT::m_strPath](#m_strpath)|Ścieżka.|

## <a name="remarks"></a>Uwagi

`CPath`, `CPathA`, i `CPathW` są wystąpieniami `CPathT` zdefiniowane w następujący sposób:

`typedef CPathT< CString > CPath;`

`typedef CPathT< CStringA > CPathA;`

`typedef CPathT< CStringW > CPathW;`

## <a name="requirements"></a>Wymagania

**Nagłówek:** atlpath.h

##  <a name="addbackslash"></a>  CPathT::AddBackslash

Wywołaj tę metodę, aby dodać ukośnik odwrotny na końcu ciągu, aby utworzyć poprawną składnię dla ścieżki. Jeśli ścieżka znajduje się już ukośnikiem odwrotnym, brak ukośnika zostaną dodane.

```
void AddBackslash();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathAddBackSlash](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddbackslasha).

##  <a name="addextension"></a>  CPathT::AddExtension

Wywołaj tę metodę, aby dodać rozszerzenie pliku do ścieżki.

```
BOOL AddExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parametry

*pszExtension*  
Rozszerzenie pliku do dodania.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathAddExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathaddextensiona).

##  <a name="append"></a>  CPathT::Append

Wywołaj tę metodę, aby dołączyć ciąg w bieżącej ścieżce.

```
BOOL Append(PCXSTR pszMore);
```

### <a name="parameters"></a>Parametry

*pszMore*  
Ciąg do dołączenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathAppend](/windows/desktop/api/shlwapi/nf-shlwapi-pathappenda).

##  <a name="buildroot"></a>  CPathT::BuildRoot

Wywołaj tę metodę, aby utworzyć ścieżkę katalogu głównego z liczbą danego dysku.

```
void BuildRoot(int iDrive);
```

### <a name="parameters"></a>Parametry

*iDrive*  
Liczba dysków (0 oznacza A:, to 1, b i tak dalej).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathBuildRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathbuildroota).

##  <a name="canonicalize"></a>  CPathT::Canonicalize

Wywołaj tę metodę, aby przekonwertować ścieżkę do postaci kanonicznej.

```
void Canonicalize();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathCanonicalize](/windows/desktop/api/shlwapi/nf-shlwapi-pathcanonicalizea).

##  <a name="combine"></a>  CPathT::Combine

Wywołaj tę metodę, aby złączyć ciąg reprezentujący nazwę katalogu i ciąg reprezentujący nazwę ścieżki pliku w jednej ścieżki.

```
void Combine(PCXSTR pszDir, PCXSTR  pszFile);
```

### <a name="parameters"></a>Parametry

*pszDir*  
Ścieżka katalogu.

*pszFile*  
Ścieżka do pliku.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathCombine](/windows/desktop/api/shlwapi/nf-shlwapi-pathcombinea).

##  <a name="commonprefix"></a>  CPathT::CommonPrefix

Wywołaj tę metodę w celu określenia, czy podana ścieżka udostępni Wspólny prefiks bieżącej ścieżce.

```
CPathT<StringType> CommonPrefix(PCXSTR pszOther);
```

### <a name="parameters"></a>Parametry

*pszOther*  
Ścieżka do porównania z bieżącym.

### <a name="return-value"></a>Wartość zwracana

Zwraca Wspólny prefiks.

### <a name="remarks"></a>Uwagi

Prefiks, który jest jednym z następujących typów: "C:\\\\",".","..",".. \\\\". Aby uzyskać więcej informacji, zobacz [PathCommonPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathcommonprefixa).

##  <a name="compactpath"></a>  CPathT::CompactPath

Wywołaj tę metodę, aby obciąć ścieżki pliku w celu dopasowania szerokość piksela podanego przez zamianę składników ścieżki elipsy.

```
BOOL CompactPath(HDC hDC, UINT nWidth);
```

### <a name="parameters"></a>Parametry

*elementu hDC*  
Kontekst urządzenia używane do miar czcionek.

*nWidth*  
Szerokość w pikselach, który ten ciąg zostanie wymuszone jego mieści się w.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathCompactPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpatha).

##  <a name="compactpathex"></a>  CPathT::CompactPathEx

Wywołaj tę metodę, aby obciąć mieścić się w danej liczby znaków, zastępując składników ścieżki wielokropek ścieżki pliku.

```
BOOL CompactPathEx(UINT nMaxChars, DWORD dwFlags = 0);
```

### <a name="parameters"></a>Parametry

*nMaxChars*  
Maksymalna liczba znaków, które mają być zawarte w nowy ciąg, w tym kończącego znaku NULL.

*Flagidw*  
Zastrzeżone.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathCompactPathEx](/windows/desktop/api/shlwapi/nf-shlwapi-pathcompactpathexa).

##  <a name="cpatht"></a>  CPathT::CPathT

Konstruktor.

```
CPathT(PCXSTR pszPath);
CPathT(const CPathT<StringType>& path);
CPathT() throw();
```

### <a name="parameters"></a>Parametry

*pszPath*  
Wskaźnik do ciągu ścieżki.

*Ścieżka*  
Ciąg ścieżki.

##  <a name="fileexists"></a>  CPathT::FileExists

Wywołaj tę metodę, aby sprawdzić, czy istnieje plik o tej nazwie ścieżki.

```
BOOL FileExists() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli plik istnieje, wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathFileExists](/windows/desktop/api/shlwapi/nf-shlwapi-pathfileexistsa).

##  <a name="findextension"></a>  CPathT::FindExtension

Wywołaj tę metodę, aby znaleźć położenie rozszerzenie pliku w ścieżce.

```
int FindExtension() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca pozycję "." poprzedzających rozszerzenia. Jeśli rozszerzenie nie zostanie znaleziona, zwraca -1.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathFindExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindextensiona).

##  <a name="findfilename"></a>  CPathT::FindFileName

Wywołaj tę metodę, aby znaleźć położenie nazwę pliku w ścieżce.

```
int FindFileName() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca pozycję nazwę pliku. Jeśli nazwa pliku nie zostanie znaleziona, zwraca -1.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathFindFileName](/windows/desktop/api/shlwapi/nf-shlwapi-pathfindfilenamea).

##  <a name="getdrivenumber"></a>  CPathT::GetDriveNumber

Wywołaj tę metodę, aby wyszukać ścieżkę do litery dysku w zakresie od "A" do "Z" i zwróć odpowiedni numer dysku.

```
int GetDriveNumber() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca liczbę dysków jako liczba całkowita z zakresu od 0 do 25 (odpowiadający "A" do "Z") jeżeli ścieżka zawiera literę dysku lub wartość -1 w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathGetDriveNumber](/windows/desktop/api/shlwapi/nf-shlwapi-pathgetdrivenumbera).

##  <a name="getextension"></a>  CPathT::GetExtension

Wywołaj tę metodę, aby pobrać rozszerzenie pliku ze ścieżki.

```
StringType GetExtension() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca rozszerzenie pliku.

##  <a name="isdirectory"></a>  CPathT::IsDirectory

Wywołaj tę metodę, aby sprawdzić, czy ścieżka jest prawidłowy katalog.

```
BOOL IsDirectory() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość niezerową (16), jeśli ścieżka jest katalogiem, wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsDirectory](/windows/desktop/api/shlwapi/nf-shlwapi-pathisdirectorya).

##  <a name="isfilespec"></a>  CPathT::IsFileSpec

Wywołanie tej metody, aby wyszukać ścieżkę znaków rozdzielający ścieżki (na przykład, ":" lub "\\"). W przypadku żadne rozdzielający ścieżki znaki nie istnieje ścieżka uważany jest za ścieżką specyfikacji pliku.

```
BOOL IsFileSpec() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli istnieją żadne rozdzielający ścieżki znaki w ścieżce, lub FAŁSZ, jeśli istnieją rozdzielający ścieżki znaków.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathisfilespeca).

##  <a name="isprefix"></a>  CPathT::IsPrefix

Wywołaj tę metodę, aby określić, czy ścieżka zawiera prawidłowy prefiks przekazany typ *pszPrefix*.

```
BOOL IsPrefix(PCXSTR pszPrefix) const;
```

### <a name="parameters"></a>Parametry

*pszPrefix*  
Prefiks do wyszukania. Prefiks, który jest jednym z następujących typów: "C:\\\\",".","..",".. \\\\".

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ścieżka zawiera prefiks lub wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsPrefix](/windows/desktop/api/shlwapi/nf-shlwapi-pathisprefixa).

##  <a name="isrelative"></a>  CPathT::IsRelative

Wywołaj tę metodę w celu ustalenia, czy ścieżka jest względna.

```
BOOL IsRelative() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli ścieżka jest względna, lub FAŁSZ, jeśli bezwzględne.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsRelative](/windows/desktop/api/shlwapi/nf-shlwapi-pathisrelativea).

##  <a name="isroot"></a>  CPathT::IsRoot

Wywołaj tę metodę w celu określenia, czy ścieżka katalogu głównego.

```
BOOL IsRoot() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ścieżka jest główny lub wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathisroota).

##  <a name="issameroot"></a>  CPathT::IsSameRoot

Wywołaj tę metodę, aby określić, czy inną ścieżkę ma typowe składnik główny przy użyciu bieżącej ścieżki.

```
BOOL IsSameRoot(PCXSTR pszOther) const;
```

### <a name="parameters"></a>Parametry

*pszOther*  
Innej ścieżki.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli oba ciągi mają ten sam składnik główny lub wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsSameRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathissameroota).

##  <a name="isunc"></a>  CPathT::IsUNC

Wywołaj tę metodę w celu ustalenia, czy ścieżka jest prawidłową ścieżkę UNC (universal Konwencja nazewnictwa) dla serwera i udostępniania.

```
BOOL IsUNC() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli ścieżka jest prawidłowa ścieżka UNC lub wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsUNC](/windows/desktop/api/shlwapi/nf-shlwapi-pathisunca).

##  <a name="isuncserver"></a>  CPathT::IsUNCServer

Wywołaj tę metodę, aby określić, czy ścieżka jest prawidłową ścieżkę UNC (universal Konwencja nazewnictwa) tylko w przypadku serwera.

```
BOOL IsUNCServer() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli ciąg jest prawidłową ścieżkę UNC tylko w przypadku serwera (Brak nazwy udziału) lub wartość FALSE w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsUNCServer](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncservera).

##  <a name="isuncservershare"></a>  CPathT::IsUNCServerShare

Wywołaj tę metodę w celu określenia, czy ścieżka jest prawidłowa ścieżka UNC (universal Konwencja nazewnictwa) udziału, \\ \  *serwera*\ *udostępnianie*.

```
BOOL IsUNCServerShare() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość PRAWDA, jeśli ścieżka znajduje się w formularzu \\ \  *serwera*\ *udostępnianie*, lub FAŁSZ, w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathIsUNCServerShare](/windows/desktop/api/shlwapi/nf-shlwapi-pathisuncserversharea).

##  <a name="m_strpath"></a>  CPathT::m_strPath

Ścieżka.

```
StringType m_strPath;
```

### <a name="remarks"></a>Uwagi

`StringType` Parametr szablonu jest `CPathT`.

##  <a name="makepretty"></a>  CPathT::MakePretty

Wywołaj tę metodę, aby przekonwertować ścieżkę, aby wszystkie małe litery, aby zapewnić spójny wygląd ścieżki.

```
BOOL MakePretty();
```

### <a name="return-value"></a>Wartość zwracana

W przeciwnym razie zwraca wartość TRUE, jeśli ścieżka została przekonwertowana, lub FAŁSZ.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathMakePretty](/windows/desktop/api/shlwapi/nf-shlwapi-pathmakeprettya).

##  <a name="matchspec"></a>  CPathT::MatchSpec

Wywołaj tę metodę, aby wyszukać ścieżkę dla ciąg zawierający typ dopasowania symboli wieloznacznych.

```
BOOL MatchSpec(PCXSTR pszSpec) const;
```

### <a name="parameters"></a>Parametry

*pszSpec*  
Wskaźnik na ciąg zakończony wartością null z typem pliku, który chcesz wyszukać. Na przykład, aby sprawdzić, czy plik w bieżącej ścieżce znajduje się plik DOC *pszSpec* powinna być ustawiona na "* .doc".

### <a name="return-value"></a>Wartość zwracana

W przeciwnym razie zwraca wartość TRUE, jeśli ciąg jest zgodny, lub FAŁSZ.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathMatchSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathmatchspeca).

##  <a name="operator_add_eq"></a>  CPathT::operator +=

Ten operator dołącza ciąg do ścieżki.

```
CPathT<StringType>& operator+=(PCXSTR pszMore);
```

### <a name="parameters"></a>Parametry

*pszMore*  
Ciąg do dołączenia.

### <a name="return-value"></a>Wartość zwracana

Zwraca ścieżkę zaktualizowane.

##  <a name="operator_const_stringtype_amp"></a>  CPathT::operator const StringType &amp;

Ten operator sprawia, że obiekt traktowane jak ciąg.

```
operatorconst StringType&() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg reprezentujący bieżącą ścieżkę, które są zarządzane przez ten obiekt.

##  <a name="operator_cpatht__pcxstr"></a>  CPathT::operator CPathT::PCXSTR

Ten operator sprawia, że obiekt traktowane jak ciąg.

```
operatorPCXSTR() const throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg reprezentujący bieżącą ścieżkę, które są zarządzane przez ten obiekt.

##  <a name="operator_stringtype__amp"></a>  CPathT::operator StringType &amp;

Ten operator sprawia, że obiekt traktowane jak ciąg.

```
operatorStringType&() throw();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca ciąg reprezentujący bieżącą ścieżkę, które są zarządzane przez ten obiekt.

##  <a name="pcxstr"></a>  CPathT::PCXSTR

Typ stałym ciągiem.

```
typedef StringType::PCXSTR PCXSTR;
```

### <a name="remarks"></a>Uwagi

`StringType` Parametr szablonu jest `CPathT`.

##  <a name="pxstr"></a>  CPathT::PXSTR

Typ ciągu.

```
typedef StringType::PXSTR PXSTR;
```

### <a name="remarks"></a>Uwagi

`StringType` Parametr szablonu jest `CPathT`.

##  <a name="quotespaces"></a>  CPathT::QuoteSpaces

Wywołaj tę metodę, aby ująć w znaki cudzysłowu ścieżkę, jeśli zawiera on żadnych spacji.

```
void QuoteSpaces();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathQuoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathquotespacesa).

##  <a name="relativepathto"></a>  CPathT::RelativePathTo

Wywołaj tę metodę, aby utworzyć ścieżkę względną z jednego pliku lub folderu.

```
BOOL RelativePathTo(
    PCXSTR pszFrom,
    DWORD dwAttrFrom,
    PCXSTR pszTo,
    DWORD dwAttrTo);
```

### <a name="parameters"></a>Parametry

*pszFrom*  
Początek ścieżki względnej.

*dwAttrFrom*  
Atrybuty pliku *pszFrom*. Jeśli ta wartość zawiera FILE_ATTRIBUTE_DIRECTORY, *pszFrom* jest zakładanego katalogiem; w przeciwnym razie *pszFrom* zakłada, że plik.

*pszTo*  
Punkt końcowy ścieżki względnej.

*dwAttrTo*  
Atrybuty pliku *pszTo*. Jeśli ta wartość zawiera FILE_ATTRIBUTE_DIRECTORY, *pszTo* jest zakładanego katalogiem; w przeciwnym razie *pszTo* zakłada, że plik.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRelativePathTo](/windows/desktop/api/shlwapi/nf-shlwapi-pathrelativepathtoa).

##  <a name="removeargs"></a>  CPathT::RemoveArgs

Wywołaj tę metodę w celu usunięcia żadnych argumentów wiersza polecenia przy użyciu ścieżki.

```
void RemoveArgs();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRemoveArgs](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveargsa).

##  <a name="removebackslash"></a>  CPathT::RemoveBackslash

Wywołaj tę metodę, aby usunąć ukośnik odwrotny na końcu ze ścieżki.

```
void RemoveBackslash();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRemoveBackslash](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovebackslasha).

##  <a name="removeblanks"></a>  CPathT::RemoveBlanks

Wywołaj tę metodę w celu usunięcia wszystkich spacji wiodących i końcowych przy użyciu ścieżki.

```
void RemoveBlanks();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRemoveBlanks](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveblanksa).

##  <a name="removeextension"></a>  CPathT::RemoveExtension

Wywołaj tę metodę, aby usunąć rozszerzenie pliku ze ścieżki, jeśli taka istnieje.

```
void RemoveExtension();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRemoveExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathremoveextensiona).

##  <a name="removefilespec"></a>  CPathT::RemoveFileSpec

Wywołaj tę metodę, aby usunąć końcowe nazwę pliku i kreski ułamkowej odwróconej ze ścieżki, jeśli je ma.

```
BOOL RemoveFileSpec();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRemoveFileSpec](/windows/desktop/api/shlwapi/nf-shlwapi-pathremovefilespeca).

##  <a name="renameextension"></a>  CPathT::RenameExtension

Wywołaj tę metodę, aby zastąpić nowego rozszerzenia rozszerzenie nazwy pliku w ścieżce. Jeśli nazwa pliku zawiera rozszerzenie, rozszerzenie zostanie dołączony do końca ścieżki.

```
BOOL RenameExtension(PCXSTR pszExtension);
```

### <a name="parameters"></a>Parametry

*pszExtension*  
Nowe rozszerzenie nazwy pliku jest poprzedzony przez "." znaków.

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE w przypadku powodzenia, wartość FALSE w przypadku niepowodzenia.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathRenameExtension](/windows/desktop/api/shlwapi/nf-shlwapi-pathrenameextensiona).

##  <a name="skiproot"></a>  CPathT::SkipRoot

Wywołaj tę metodę można przeanalizować ścieżki, ignorowanie literę dysku i części ścieżki serwera/udział UNC (universal Konwencja nazewnictwa).

```
int SkipRoot() const;
```

### <a name="return-value"></a>Wartość zwracana

Zwraca pozycję początku podrzędną, która następuje po katalogu głównego (literę dysku lub udziale serwera UNC).

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathSkipRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathskiproota).

##  <a name="strippath"></a>  CPathT::StripPath

Wywołaj tę metodę, aby usunąć część ścieżki pełną ścieżkę i nazwę pliku.

```
void StripPath();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathStripPath](/windows/desktop/api/shlwapi/nf-shlwapi-pathstrippatha).

##  <a name="striptoroot"></a>  CPathT::StripToRoot

Wywołaj tę metodę, aby usunąć wszystkie części ścieżki, z wyjątkiem informacji katalogu głównego.

```
BOOL StripToRoot();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość TRUE, jeśli prawidłową literę dysku został znaleziony w ścieżce, lub FAŁSZ w przeciwnym razie.

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathStripToRoot](/windows/desktop/api/shlwapi/nf-shlwapi-pathstriptoroota).

##  <a name="unquotespaces"></a>  CPathT::UnquoteSpaces

Wywołaj tę metodę, aby usunąć znaki cudzysłowu na początku i końca ścieżki.

```
void UnquoteSpaces();
```

### <a name="remarks"></a>Uwagi

Aby uzyskać więcej informacji, zobacz [PathUnquoteSpaces](/windows/desktop/api/shlwapi/nf-shlwapi-pathunquotespacesa).

##  <a name="xchar"></a>  CPathT::XCHAR

Typ znaku.

```
typedef StringType::XCHAR XCHAR;
```

### <a name="remarks"></a>Uwagi

`StringType` Parametr szablonu jest `CPathT`.

## <a name="see-also"></a>Zobacz też

[Klasy](../../atl/reference/atl-classes.md)   
[CStringT, klasa](../../atl-mfc-shared/reference/cstringt-class.md)