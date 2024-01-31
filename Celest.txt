--
-- PostgreSQL database dump
--

-- Dumped from database version 12.9 (Ubuntu 12.9-2.pgdg20.04+1)
-- Dumped by pg_dump version 12.9 (Ubuntu 12.9-2.pgdg20.04+1)

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

DROP DATABASE universe;
--
-- Name: universe; Type: DATABASE; Schema: -; Owner: freecodecamp
--

CREATE DATABASE universe WITH TEMPLATE = template0 ENCODING = 'UTF8' LC_COLLATE = 'C.UTF-8' LC_CTYPE = 'C.UTF-8';


ALTER DATABASE universe OWNER TO freecodecamp;

\connect universe

SET statement_timeout = 0;
SET lock_timeout = 0;
SET idle_in_transaction_session_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SELECT pg_catalog.set_config('search_path', '', false);
SET check_function_bodies = false;
SET xmloption = content;
SET client_min_messages = warning;
SET row_security = off;

SET default_tablespace = '';

SET default_table_access_method = heap;

--
-- Name: galaxy; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.galaxy (
    galaxy_id integer NOT NULL,
    name character varying(35) NOT NULL,
    distance_kpc integer,
    right_ascension_h integer,
    constellation character varying(35),
    redshift numeric
);


ALTER TABLE public.galaxy OWNER TO freecodecamp;

--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.galaxy_galaxy_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.galaxy_galaxy_id_seq OWNER TO freecodecamp;

--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.galaxy_galaxy_id_seq OWNED BY public.galaxy.galaxy_id;


--
-- Name: moon; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.moon (
    moon_id integer NOT NULL,
    name character varying(35) NOT NULL,
    is_spherical boolean DEFAULT true,
    planet_id integer,
    discovery_year integer
);


ALTER TABLE public.moon OWNER TO freecodecamp;

--
-- Name: moon_moon_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.moon_moon_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.moon_moon_id_seq OWNER TO freecodecamp;

--
-- Name: moon_moon_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.moon_moon_id_seq OWNED BY public.moon.moon_id;


--
-- Name: painting; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.painting (
    name character varying(35) NOT NULL,
    year_created integer,
    painting_id integer NOT NULL
);


ALTER TABLE public.painting OWNER TO freecodecamp;

--
-- Name: planet; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.planet (
    planet_id integer NOT NULL,
    name character varying(35) NOT NULL,
    has_life boolean DEFAULT false,
    star_id integer,
    type_by_composition character varying(35)
);


ALTER TABLE public.planet OWNER TO freecodecamp;

--
-- Name: planet_planet_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.planet_planet_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.planet_planet_id_seq OWNER TO freecodecamp;

--
-- Name: planet_planet_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.planet_planet_id_seq OWNED BY public.planet.planet_id;


--
-- Name: space_themed_paintings_painting_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.space_themed_paintings_painting_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.space_themed_paintings_painting_id_seq OWNER TO freecodecamp;

--
-- Name: space_themed_paintings_painting_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.space_themed_paintings_painting_id_seq OWNED BY public.painting.painting_id;


--
-- Name: star; Type: TABLE; Schema: public; Owner: freecodecamp
--

CREATE TABLE public.star (
    star_id integer NOT NULL,
    name character varying(35) NOT NULL,
    description text,
    galaxy_id integer,
    temperature_kelvin integer
);


ALTER TABLE public.star OWNER TO freecodecamp;

--
-- Name: star_star_id_seq; Type: SEQUENCE; Schema: public; Owner: freecodecamp
--

CREATE SEQUENCE public.star_star_id_seq
    AS integer
    START WITH 1
    INCREMENT BY 1
    NO MINVALUE
    NO MAXVALUE
    CACHE 1;


ALTER TABLE public.star_star_id_seq OWNER TO freecodecamp;

--
-- Name: star_star_id_seq; Type: SEQUENCE OWNED BY; Schema: public; Owner: freecodecamp
--

ALTER SEQUENCE public.star_star_id_seq OWNED BY public.star.star_id;


--
-- Name: galaxy galaxy_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy ALTER COLUMN galaxy_id SET DEFAULT nextval('public.galaxy_galaxy_id_seq'::regclass);


--
-- Name: moon moon_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon ALTER COLUMN moon_id SET DEFAULT nextval('public.moon_moon_id_seq'::regclass);


--
-- Name: painting painting_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.painting ALTER COLUMN painting_id SET DEFAULT nextval('public.space_themed_paintings_painting_id_seq'::regclass);


--
-- Name: planet planet_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet ALTER COLUMN planet_id SET DEFAULT nextval('public.planet_planet_id_seq'::regclass);


--
-- Name: star star_id; Type: DEFAULT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star ALTER COLUMN star_id SET DEFAULT nextval('public.star_star_id_seq'::regclass);


--
-- Data for Name: galaxy; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.galaxy VALUES (1, 'Milky Way', 8, 17, 'Sagittarius', 0);
INSERT INTO public.galaxy VALUES (2, 'Messier 58', 19100, 12, 'Virgo', 0.00506);
INSERT INTO public.galaxy VALUES (3, 'Messier 65', 12880, 11, 'Leo', 0.002692);
INSERT INTO public.galaxy VALUES (4, 'Messier 66', 9600, 11, 'Leo', 0.002425);
INSERT INTO public.galaxy VALUES (6, 'Messier 83', 4500, 13, 'Hydra', 0.001721);
INSERT INTO public.galaxy VALUES (7, 'Andromeda', 765, 0, 'Andromeda', -0.001004);


--
-- Data for Name: moon; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.moon VALUES (1, 'Moon', true, 1, NULL);
INSERT INTO public.moon VALUES (2, 'Phobos', false, 4, 1877);
INSERT INTO public.moon VALUES (3, 'Demois', false, 4, 1877);
INSERT INTO public.moon VALUES (4, 'Naiad', false, 8, 1989);
INSERT INTO public.moon VALUES (5, 'Thalassa', false, 8, 1989);
INSERT INTO public.moon VALUES (6, 'Despina', false, 8, 1989);
INSERT INTO public.moon VALUES (7, 'Galatea', false, 8, 1989);
INSERT INTO public.moon VALUES (8, 'Larissa', false, 8, 1981);
INSERT INTO public.moon VALUES (9, 'Hippocamp', false, 8, 2013);
INSERT INTO public.moon VALUES (10, 'Proteus', false, 8, 1989);
INSERT INTO public.moon VALUES (11, 'Triton', NULL, 8, 1846);
INSERT INTO public.moon VALUES (12, 'Nereid', NULL, 8, 1949);
INSERT INTO public.moon VALUES (13, 'Halimede', NULL, 8, 2002);
INSERT INTO public.moon VALUES (14, 'Sao', NULL, 8, 2002);
INSERT INTO public.moon VALUES (15, 'Laomedia', NULL, 8, 2002);
INSERT INTO public.moon VALUES (16, 'Psamathe', NULL, 8, 2003);
INSERT INTO public.moon VALUES (17, 'Neso', NULL, 8, 2002);
INSERT INTO public.moon VALUES (18, 'Charon', true, 11, 1978);
INSERT INTO public.moon VALUES (19, 'Styx', false, 11, 2012);
INSERT INTO public.moon VALUES (20, 'Nix', false, 11, 2005);


--
-- Data for Name: painting; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.painting VALUES ('The Starry Night', 1889, 1);
INSERT INTO public.painting VALUES ('Starry Night Over the Rhone', 1888, 2);
INSERT INTO public.painting VALUES ('Whirlpool Galaxy Sketch', 1845, 3);


--
-- Data for Name: planet; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.planet VALUES (1, 'Earth', true, 2, 'terestrial');
INSERT INTO public.planet VALUES (2, 'Mercury', false, 2, 'terestrial');
INSERT INTO public.planet VALUES (3, 'Venus', false, 2, 'terestrial');
INSERT INTO public.planet VALUES (4, 'Mars', false, 2, 'terestrial');
INSERT INTO public.planet VALUES (5, 'Jupiter', false, 2, 'gas giant');
INSERT INTO public.planet VALUES (6, 'Saturn', false, 2, 'gas giant');
INSERT INTO public.planet VALUES (7, 'Uranus', false, 2, 'gasice giant');
INSERT INTO public.planet VALUES (8, 'Neptune', false, 2, 'gasice giant');
INSERT INTO public.planet VALUES (9, 'Ceres', false, 2, 'dwarf');
INSERT INTO public.planet VALUES (10, 'Orcus', false, 2, 'dwarf');
INSERT INTO public.planet VALUES (11, 'Pluto', false, 2, 'dwarf');
INSERT INTO public.planet VALUES (12, 'Haumea', false, 2, 'dwarf');
INSERT INTO public.planet VALUES (13, 'Quaoar', false, 2, 'dwarf');
INSERT INTO public.planet VALUES (14, 'Makemake', false, 2, 'dwarf');
INSERT INTO public.planet VALUES (15, 'Gonggong', false, 2, 'dwarf');
INSERT INTO public.planet VALUES (16, 'Eris', false, 2, 'dwarf');
INSERT INTO public.planet VALUES (17, 'Sedna', false, 2, 'dwarf');


--
-- Data for Name: star; Type: TABLE DATA; Schema: public; Owner: freecodecamp
--

INSERT INTO public.star VALUES (1, 'Bernard''s Star', 'might be among the oldest stars in the Milky Way galaxy', 1, 3223);
INSERT INTO public.star VALUES (2, 'Sun', 'The Sun is by far the brightest object in the Earth''s sky', 1, 5772);
INSERT INTO public.star VALUES (4, 'Proxima Centauri', 'is the nearest-known star to the Sun', 1, 2992);
INSERT INTO public.star VALUES (5, 'Luhman 16', 'they are actually 2 suns', 1, 1280);
INSERT INTO public.star VALUES (6, 'WISE 0855−0714', 'The WISE object was detected in March 2013', 1, 250);
INSERT INTO public.star VALUES (7, 'Wolf 359', 'Its proximity to Earth has led to its mention in several works of fiction', 1, 2749);


--
-- Name: galaxy_galaxy_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.galaxy_galaxy_id_seq', 7, true);


--
-- Name: moon_moon_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.moon_moon_id_seq', 20, true);


--
-- Name: planet_planet_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.planet_planet_id_seq', 17, true);


--
-- Name: space_themed_paintings_painting_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.space_themed_paintings_painting_id_seq', 3, true);


--
-- Name: star_star_id_seq; Type: SEQUENCE SET; Schema: public; Owner: freecodecamp
--

SELECT pg_catalog.setval('public.star_star_id_seq', 7, true);


--
-- Name: galaxy galaxy_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_name_key UNIQUE (name);


--
-- Name: galaxy galaxy_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.galaxy
    ADD CONSTRAINT galaxy_pkey PRIMARY KEY (galaxy_id);


--
-- Name: moon moon_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_name_key UNIQUE (name);


--
-- Name: moon moon_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_pkey PRIMARY KEY (moon_id);


--
-- Name: planet planet_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_name_key UNIQUE (name);


--
-- Name: planet planet_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_pkey PRIMARY KEY (planet_id);


--
-- Name: painting space_themed_paintings_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.painting
    ADD CONSTRAINT space_themed_paintings_name_key UNIQUE (name);


--
-- Name: painting space_themed_paintings_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.painting
    ADD CONSTRAINT space_themed_paintings_pkey PRIMARY KEY (painting_id);


--
-- Name: star star_name_key; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_name_key UNIQUE (name);


--
-- Name: star star_pkey; Type: CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_pkey PRIMARY KEY (star_id);


--
-- Name: moon moon_planet_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.moon
    ADD CONSTRAINT moon_planet_id_fkey FOREIGN KEY (planet_id) REFERENCES public.planet(planet_id);


--
-- Name: planet planet_star_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.planet
    ADD CONSTRAINT planet_star_id_fkey FOREIGN KEY (star_id) REFERENCES public.star(star_id);


--
-- Name: star star_galaxy_id_fkey; Type: FK CONSTRAINT; Schema: public; Owner: freecodecamp
--

ALTER TABLE ONLY public.star
    ADD CONSTRAINT star_galaxy_id_fkey FOREIGN KEY (galaxy_id) REFERENCES public.galaxy(galaxy_id);


--
-- PostgreSQL database dump complete
--

