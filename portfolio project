SELECT * FROM project.dbo.Data1;
SELECT * FROM project.dbo.Data2;

--number of rows in data set

select count(*) from project.dbo.Data1;
select count(*) from project.dbo.Data1;

--data set for Jharkhan and Bihar

select * from project.dbo.Data1 where State in ('Jharkhand', 'Bihar'); 

--total population

select sum(Population) AS Population from project.dbo.Data2;

-- Avg growth of India

select avg(growth)*100 as avg_growth from project.dbo.Data1; 

-- Avg growth of each state
select state,avg(growth)*100 as avg_growth from project.dbo.Data1 group by state; 


--Avg sex ratio for every state

select state, round(avg(sex_ratio)*100,0) as avg_sex_ratio from project.dbo.data1 group by state order by avg_sex_ratio desc;


--aveg literacy rate


select state, round(avg(literacy),0) as avg_literacy_ratio from project.dbo.data1 group by state order by avg_literacy_ratio desc;

--literacy ratio greater than 90

select state, round(avg(literacy),0) as avg_literacy_ratio from project.dbo.data1 


group by state having round(avg(literacy),0) > 90  order by avg_literacy_ratio desc  ;

-- top 3 states showing highest growth ratio

select top 3 state, avg(growth)*100 as avg_growth from project.dbo.data1 group by state order by avg_growth desc;

--bottom 3 states showing highest sex ratio

select top 3 state, round(avg(sex_ratio),0) as avg_sex_ratio from project.dbo.data1 where state is not null group by state order by avg_sex_ratio asc; 


-- top and bottom 3 states in the literacy rate 

drop table if exists #topstate;
create table #topstate
( state nvarchar(255),
topstate float

)

insert into #topstate 
select state, round(avg(literacy),0) as avg_literacy_ratio from project.dbo.data1 group by state order by avg_literacy_ratio desc;


 select top 3 * from #topstate order by #topstate.topstate desc ;

drop table if exists #bottomstate;
create table #bottomstate
( state nvarchar(255),
bottomstate float

)

insert into #bottomstate
select state, round(avg(literacy),0) as avg_literacy_ratio from project.dbo.data1 group by state order by avg_literacy_ratio asc;


 select top 3 * from #bottomstate order by #bottomstate.bottomstate asc ;

 -- combining both results in a single table using union 

 select * from (
 select top 3 * from #topstate order by #topstate.topstate desc )  a
 union
 select * from (
 select top 3 * from #bottomstate order by #bottomstate.bottomstate asc) b;

 -- state names starting with a

 select distinct state from project.dbo.data1 where lower(state) like 'a%' or lower(state) like 'b%' ;

