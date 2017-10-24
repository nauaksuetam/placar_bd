create schema db;
use db;

create table clubes( id bigint primary key auto_increment not null unique, nome varchar(100) not null, escudo varchar (200) not null);
create table estadios( id bigint primary key auto_increment not null unique, nome varchar(100) not null);
create table rodadas(id bigint primary key auto_increment not null unique, descricao varchar(20)not null);
create table placar ( id bigint primary key auto_increment not null unique, dt_jogo date not null, mandante_id bigint not null, gol_mandante int not null, cartao varchar (10) not null, clube_id bigint not null, visitante_id bigint not null, gol_visitante int not null, estadio_id bigint not null, rodada_id bigint not null, foreign key (clubes_id) references clube(id)on delete no action on update no action , foreign key (estadio_id) references estadio(id)on delete no action on update no action , foreign key (rodada_id) references rodada(id)on delete no action on update no action , foreign key (mandante_id,visitante_id) references clubes(id)on delete no action on update no action);
create table jogadores(id bigint primary key auto_increment unique, nome varchar(100), clubes_id bigint not null, foreign key (jogador_id) references clubes(id));
create table jogador_placar( jogador_id bigint primary key auto_increment not null unique, cartao varchar(10) not null, gols int not null, foreign key (jogador_placar) references placar(id)on delete no action on update no action ); 
alter table placar add fk_rodada_id bigint;
alter table placar add constraint fk_rodada_id
foreign key (fk_rodada_id) references rodada (id_rodada);



insert into clubes(id, nome, sigla, escudo) values(1,'Fluminense','FLU','globoesporte.com/clubes/escudos/flu.svg'),(2,'Palmeiras','PAL','globoesporte.com/clubes/escudos/pal.svg');

insert into estadio values (1,'Maracanã');
insert into rodadas values (1,'Rodada 25');
insert into placares values (1,'2017-09-24 16:00:00',0,1,1,2,1,1); 
insert into placares values(dt_jogo date) values (24-09-17);
insert into placares values(mandante_id) values (fluminense);
insert into placares values(visitante_id) values(palmeiras);
