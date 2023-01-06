select * 
from PortfolioProject..CovidDeaths
where continent is not null
order by 3,4

--select * 
--from PortfolioProject..CovidVaccinations
--order by 3,4

Select Location, date, total_cases, new_cases, total_deaths, population
from PortfolioProject..CovidDeaths
where continent is not null
order by 1,2

-- Looking at Total Cases vs Total Deaths
-- Shows percentage of dying if you had covid

Select Location, date, total_cases, total_deaths, (Total_deaths/total_cases*100) as DeathPercentage
from PortfolioProject..CovidDeaths
where location like '%Mexico%'
and continent is not null
order by 1,2

-- Looking at Total Cases vs Population
-- Shows what percentage of population got Covid

Select Location, date, Population, total_cases, (total_cases/population*100) as PercentPopulationInfected
from PortfolioProject..CovidDeaths
-- where location like '%Mexico%'
where continent is not null
order by 1,2

-- Looking at Countries with Highest infection rates compared to population

Select Location, Population, MAX(total_cases) as HighestInfectionCount, MAX((total_cases/population*100)) as PercentPopulationInfected
from PortfolioProject..CovidDeaths
-- where location like '%Mexico%'
where continent is not null
group by  location, population
order by PercentPopulationInfected desc

-- Showing countries with Highest Death Count per Population

Select Location, MAX(cast(Total_deaths as int)) as TotalDeathCount
from PortfolioProject..CovidDeaths
-- where location like '%Mexico%'
where continent is not null
group by  location
order by TotalDeathCount desc

-- Showing continents with Highest Death Count per Population

Select location, MAX(cast(Total_deaths as int)) as TotalDeathCount
from PortfolioProject..CovidDeaths
-- where location like '%Mexico%'
where continent is null
group by  location
order by TotalDeathCount desc


-- Global Numbers

Select date, SUM(new_cases) as total_cases, SUM(cast(new_deaths as int)) as total_deaths, SUM(cast(new_deaths as int))/SUM(new_cases)*100 as DeathPercentage
from PortfolioProject..CovidDeaths
-- where location like '%Mexico%'
where continent is not null
group by date
order by 1,2

Select SUM(new_cases) as total_cases, SUM(cast(new_deaths as int)) as total_deaths, SUM(cast(new_deaths as int))/SUM(new_cases)*100 as DeathPercentage
from PortfolioProject..CovidDeaths
-- where location like '%Mexico%'
where continent is not null
-- group by date
order by 1,2


-- Looking at Total Population vs Vaccinations

Select dea.continent, dea.location, dea.date, population, vac.new_vaccinations
, SUM(CONVERT(int,vac.new_vaccinations)) OVER (Partition by dea.location order by dea.location, dea.date) as TotalNewVaccinations
--, (TotalNewVaccinations/population)*100
From PortfolioProject..CovidDeaths dea
Join PortfolioProject..CovidVaccinations vac
	On dea.location = vac.location
	and dea.date = vac.date
where dea.continent is not null
order by 2,3

-- USE CTE

With PopvsVac (continent, location, date, population, new_vaccinations, TotalNewVaccinations)
as
(
Select dea.continent, dea.location, dea.date, population, vac.new_vaccinations
, SUM(CONVERT(int,vac.new_vaccinations)) OVER (Partition by dea.location order by dea.location, dea.date) as TotalNewVaccinations
--, (TotalNewVaccinations/population)*100
From PortfolioProject..CovidDeaths dea
Join PortfolioProject..CovidVaccinations vac
	On dea.location = vac.location
	and dea.date = vac.date
where dea.continent is not null
-- order by 2,3
)
select *, (TotalNewVaccinations/population)*100 as VaccinatedPercentage
from PopvsVac

-- USE TEMP TABLE

DROP Table if exists #VaccinatedPercentage  --(in case you want to make a modification)
Create Table #VaccinatedPercentage
(
Continent nvarchar(255),
Location nvarchar(255),
Date datetime,
Population numeric,
New_vaccinations numeric,
TotalNewVaccinations numeric
)
Insert into #VaccinatedPercentage
Select dea.continent, dea.location, dea.date, population, vac.new_vaccinations
, SUM(CONVERT(int,vac.new_vaccinations)) OVER (Partition by dea.location order by dea.location, dea.date) as TotalNewVaccinations
--, (TotalNewVaccinations/population)*100
From PortfolioProject..CovidDeaths dea
Join PortfolioProject..CovidVaccinations vac
	On dea.location = vac.location
	and dea.date = vac.date
where dea.continent is not null
-- order by 2,3

select *, (TotalNewVaccinations/population)*100 as VaccinatedPercentage
from #VaccinatedPercentage


-- Creating view to store data for later visualizations

Create View VaccinatedPercentage as
Select dea.continent, dea.location, dea.date, population, vac.new_vaccinations
, SUM(CONVERT(int,vac.new_vaccinations)) OVER (Partition by dea.location order by dea.location, dea.date) as TotalNewVaccinations
--, (TotalNewVaccinations/population)*100
From PortfolioProject..CovidDeaths dea
Join PortfolioProject..CovidVaccinations vac
	On dea.location = vac.location
	and dea.date = vac.date
where dea.continent is not null
-- order by 2,3

Select *
From VaccinatedPercentage


Create View DeathPercentage as
Select Location, date, total_cases, total_deaths, (Total_deaths/total_cases*100) as DeathPercentage
from PortfolioProject..CovidDeaths
-- where location like '%Mexico%'
where continent is not null
-- order by 1,2

Create View PercentPopulationInfected as
Select Location, date, Population, total_cases, (total_cases/population*100) as PercentPopulationInfected
from PortfolioProject..CovidDeaths
-- where location like '%Mexico%'
where continent is not null
-- order by 1,2

Create View TotalDeathCountCountries as
Select Location, MAX(cast(Total_deaths as int)) as TotalDeathCount
from PortfolioProject..CovidDeaths
-- where location like '%Mexico%'
where continent is not null
group by  location
-- order by TotalDeathCount desc

Create View TotalDeathCountContinents as
Select location, MAX(cast(Total_deaths as int)) as TotalDeathCount
from PortfolioProject..CovidDeaths
-- where location like '%Mexico%'
where continent is null
group by  location
-- order by TotalDeathCount desc

Create View InfectedPopulationPercentage as
Select Location, Population, MAX(total_cases) as HighestInfectionCount, MAX((total_cases/population*100)) as PercentPopulationInfected
from PortfolioProject..CovidDeaths
-- where location like '%Mexico%'
where continent is not null
group by  location, population
-- order by PercentPopulationInfected desc
