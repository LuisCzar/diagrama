``mermaid 
classDiagram
    %% Classe abstrata base
    class AbstractEntity {
        -Long id
        +AbstractEntity()
        +getId() Long
        +setId(Long id) void
        +hashCode() int
        +equals(Object obj) boolean
        +toString() String
    }

    %% Enumeração para tipos de perfil
    class PerfilTipo {
        <<enumeration>>
        +ADMIN
        +MEDICO
        +PACIENTE
        -long cod
        -String desc
        +PerfilTipo(long cod, String desc)
        +getCod() long
        +setCod(long cod) void
        +getDesc() String
        +setDesc(String desc) void
    }

    %% Classe de usuário
    class Usuario {
        -String email
        -String senha
        -List~Perfil~ perfis
        -boolean ativo
        -String codigoVerificador
        +Usuario()
        +Usuario(Long id)
        +getEmail() String
        +setEmail(String email) void
        +getSenha() String
        +setSenha(String senha) void
        +getPerfis() List~Perfil~
        +setPerfis(List~Perfil~ perfis) void
        +isAtivo() boolean
        +setAtivo(boolean ativo) void
        +getCodigoVerificador() String
        +setCodigoVerificador(String codigoVerificador) void
        +hashCode() int
        +equals(Object obj) boolean
        +toString() String
    }

    %% Classe de perfil
    class Perfil {
        -String descricao
        +Perfil()
        +Perfil(Long id)
        +getDescricao() String
        +setDescricao(String descricao) void
        +hashCode() int
        +equals(Object obj) boolean
        +toString() String
    }

    %% Classe de médico
    class Medico {
        -String nome
        -Integer crm
        -LocalDate dtInscricao
        -Set~Especialidade~ especialidades
        -List~Agendamento~ agendamentos
        -Usuario usuario
        +Medico()
        +Medico(Long id)
        +getNome() String
        +setNome(String nome) void
        +getCrm() Integer
        +setCrm(Integer crm) void
        +getDtInscricao() LocalDate
        +setDtInscricao(LocalDate dtInscricao) void
        +getEspecialidades() Set~Especialidade~
        +setEspecialidades(Set~Especialidade~ especialidades) void
        +getAgendamentos() List~Agendamento~
        +setAgendamentos(List~Agendamento~ agendamentos) void
        +getUsuario() Usuario
        +setUsuario(Usuario usuario) void
        +hashCode() int
        +equals(Object obj) boolean
        +toString() String
    }

    %% Classe de paciente
    class Paciente {
        -String nome
        -LocalDate dtNascimento
        -List~Agendamento~ agendamentos
        -Usuario usuario
        +Paciente()
        +Paciente(Long id)
        +getNome() String
        +setNome(String nome) void
        +getDtNascimento() LocalDate
        +setDtNascimento(LocalDate dtNascimento) void
        +getAgendamentos() List~Agendamento~
        +setAgendamentos(List~Agendamento~ agendamentos) void
        +getUsuario() Usuario
        +setUsuario(Usuario usuario) void
        +hashCode() int
        +equals(Object obj) boolean
        +toString() String
    }

    %% Classe de especialidade
    class Especialidade {
        -String titulo
        -String descricao
        -List~Medico~ medicos
        +Especialidade()
        +Especialidade(Long id)
        +getTitulo() String
        +setTitulo(String titulo) void
        +getDescricao() String
        +setDescricao(String descricao) void
        +getMedicos() List~Medico~
        +setMedicos(List~Medico~ medicos) void
        +hashCode() int
        +equals(Object obj) boolean
        +toString() String
    }

    %% Classe de agendamento
    class Agendamento {
        -Especialidade especialidade
        -Medico medico
        -Paciente paciente
        -Horario horario
        -LocalDate dataConsulta
        +getEspecialidade() Especialidade
        +setEspecialidade(Especialidade especialidade) void
        +getMedico() Medico
        +setMedico(Medico medico) void
        +getPaciente() Paciente
        +setPaciente(Paciente paciente) void
        +getHorario() Horario
        +setHorario(Horario horario) void
        +getDataConsulta() LocalDate
        +setDataConsulta(LocalDate dataConsulta) void
        +hashCode() int
        +equals(Object obj) boolean
        +toString() String
    }

    %% Classe de horário
    class Horario {
        -LocalTime horaMinuto
        +getHoraMinuto() LocalTime
        +setHoraMinuto(LocalTime horaMinuto) void
        +hashCode() int
        +equals(Object obj) boolean
        +toString() String
    }

    %% Relacionamentos de herança
    AbstractEntity <|-- Usuario : extends
    AbstractEntity <|-- Perfil : extends
    AbstractEntity <|-- Medico : extends
    AbstractEntity <|-- Paciente : extends
    AbstractEntity <|-- Especialidade : extends
    AbstractEntity <|-- Agendamento : extends
    AbstractEntity <|-- Horario : extends

    %% Relacionamentos de associação
    Usuario ||--o{ Perfil : "tem muitos"
    Medico ||--|| Usuario : "possui um"
    Paciente ||--|| Usuario : "possui um"
    Medico ||--o{ Especialidade : "tem muitas"
    Especialidade ||--o{ Medico : "tem muitos"
    Medico ||--o{ Agendamento : "tem muitos"
    Paciente ||--o{ Agendamento : "tem muitos"
    Especialidade ||--o{ Agendamento : "tem muitos"
    Horario ||--o{ Agendamento : "tem muitos"

```
