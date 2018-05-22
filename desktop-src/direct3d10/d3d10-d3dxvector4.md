﻿---
Description: 'Describes a four-component vector including operator overloads and type casts.'
ms.assetid: 'c6348346-f317-48ed-a369-e39fdb4dc1d6'
title: D3DXVECTOR4 structure
---

# D3DXVECTOR4 structure

Describes a four-component vector including operator overloads and type casts.

## Syntax


```C++
typedef struct D3DXVECTOR4 {
  FLOAT x;
  FLOAT y;
  FLOAT z;
  FLOAT w;
} D3DXVECTOR4, *LPD3DXVECTOR4;
```



## Members

<dl> <dt>

**x**
</dt> <dd>

Type: **[**FLOAT**](winprog.windows_data_types)**

</dd> <dd>

The x-component.

</dd> <dt>

**y**
</dt> <dd>

Type: **[**FLOAT**](winprog.windows_data_types)**

</dd> <dd>

The y-component.

</dd> <dt>

**z**
</dt> <dd>

Type: **[**FLOAT**](winprog.windows_data_types)**

</dd> <dd>

The z-component.

</dd> <dt>

**w**
</dt> <dd>

Type: **[**FLOAT**](winprog.windows_data_types)**

</dd> <dd>

The w-component.

</dd> </dl>

## Remarks

**D3DXVECTOR4** has the following C++ extensions.

### D3DXVECTOR4 Extensions


```
typedef struct D3DXVECTOR4
{
#ifdef __cplusplus
public:
    D3DXVECTOR4() {};
    D3DXVECTOR4( CONST FLOAT* );
    D3DXVECTOR4( CONST D3DXFLOAT16 * );
    D3DXVECTOR4( CONST D3DVECTOR&amp; xyz, FLOAT w );
    D3DXVECTOR4( FLOAT x, FLOAT y, FLOAT z, FLOAT w );

    // casting
    operator FLOAT* ();
    operator CONST FLOAT* () const;

    // assignment operators
    D3DXVECTOR4&amp; operator += ( CONST D3DXVECTOR4&amp; );
    D3DXVECTOR4&amp; operator -= ( CONST D3DXVECTOR4&amp; );
    D3DXVECTOR4&amp; operator *= ( FLOAT );
    D3DXVECTOR4&amp; operator /= ( FLOAT );

    // unary operators
    D3DXVECTOR4 operator + () const;
    D3DXVECTOR4 operator - () const;

    // binary operators
    D3DXVECTOR4 operator + ( CONST D3DXVECTOR4&amp; ) const;
    D3DXVECTOR4 operator - ( CONST D3DXVECTOR4&amp; ) const;
    D3DXVECTOR4 operator * ( FLOAT ) const;
    D3DXVECTOR4 operator / ( FLOAT ) const;

    friend D3DXVECTOR4 operator * ( FLOAT, CONST D3DXVECTOR4&amp; );

    BOOL operator == ( CONST D3DXVECTOR4&amp; ) const;
    BOOL operator != ( CONST D3DXVECTOR4&amp; ) const;

public:
#endif //__cplusplus
    FLOAT x, y, z, w;
} D3DXVECTOR4, *LPD3DXVECTOR4;
        
```



## Requirements



|                   |                                                                                         |
|-------------------|-----------------------------------------------------------------------------------------|
| Header<br/> | <dl> <dt>D3DX10Math.h</dt> </dl> |



## See also

<dl> <dt>

[D3DX Structures](d3d10-graphics-reference-d3dx10-structures.md)
</dt> </dl>

 

 



