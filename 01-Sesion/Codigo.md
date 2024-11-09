# Entity 

## `Cliente`

```java
package com.Corhuila.Parque.Entity;

import jakarta.persistence.*;

@Entity
@Table(name = "cliente")
public class Cliente {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Integer id;

    @Column(name = "documento", length = 50, nullable = false)
    private String documento;

    @Column(name = "nombre", length = 50, nullable = false)
    private String nombre;

    @Column(name = "correo", length = 40, nullable = false)
    private String correo;

    public Integer getId() {
        return id;
    }

    public void setId(Integer id) {
        this.id = id;
    }

    public String getDocumento() {
        return documento;
    }

    public void setDocumento(String documento) {
        this.documento = documento;
    }

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public String getCorreo() {
        return correo;
    }

    public void setCorreo(String correo) {
        this.correo = correo;
    }
}

```

## `Servicio`

```java
package com.Corhuila.Parque.Entity;

import jakarta.persistence.*;

import java.math.BigDecimal;

@Entity
@Table(name = "servicio")
public class Servicio {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Integer id;

    @Column(name = "codigo", length = 10, nullable = false)
    private String codigo;

    @Column(name = "nombre", length = 50, nullable = false)
    private String nombre;

    @Column(name = "precio_unitario", nullable = false, precision = 10, scale = 2)
    private BigDecimal precioUnitario;

    public Integer getId() {
        return id;
    }

    public void setId(Integer id) {
        this.id = id;
    }

    public String getCodigo() {
        return codigo;
    }

    public void setCodigo(String codigo) {
        this.codigo = codigo;
    }

    public String getNombre() {
        return nombre;
    }

    public void setNombre(String nombre) {
        this.nombre = nombre;
    }

    public BigDecimal getPrecioUnitario() {
        return precioUnitario;
    }

    public void setPrecioUnitario(BigDecimal precioUnitario) {
        this.precioUnitario = precioUnitario;
    }
}
```

## `ServicioCliente`

```java
package com.Corhuila.Parque.Entity;

import jakarta.persistence.*;

import java.math.BigDecimal;

@Entity
@Table(name = "servicio_cliente")
public class ServicioCliente {
    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Integer id;

    @Column(name = "cantidad", nullable = false)
    private Integer cantidad;

    @Column(name = "total_pagar", nullable = false, precision = 10, scale = 2)
    private BigDecimal totalPagar;

    @ManyToOne(fetch = FetchType.EAGER, optional = false)
    @JoinColumn(name = "cliente_id")
    private Cliente clienteId;

    @ManyToOne(fetch = FetchType.EAGER, optional = false)
    @JoinColumn(name = "servicio_id")
    private Servicio servicioId;

    public Integer getId() {
        return id;
    }

    public void setId(Integer id) {
        this.id = id;
    }

    public Integer getCantidad() {
        return cantidad;
    }

    public void setCantidad(Integer cantidad) {
        this.cantidad = cantidad;
    }

    public BigDecimal getTotalPagar() {
        return totalPagar;
    }

    public void setTotalPagar(BigDecimal totalPagar) {
        this.totalPagar = totalPagar;
    }

    public Cliente getClienteId() {
        return clienteId;
    }

    public void setClienteId(Cliente clienteId) {
        this.clienteId = clienteId;
    }

    public Servicio getServicioId() {
        return servicioId;
    }

    public void setServicioId(Servicio servicioId) {
        this.servicioId = servicioId;
    }
}
```
