noise-rs
========

[![Build Status](https://travis-ci.org/bjz/noise-rs.png)](https://travis-ci.org/bjz/noise-rs)


Procedural noise generation library for Rust.

API
===

The API is currently being revamped to a simple, composable closure-based system.

Implemented thus far
--------------------

~~~rust
struct Seed { ... }
Seed {
    fn new(seed: u32) -> Seed;
}

pub type Point2<T> = [T, ..2];
pub type Point3<T> = [T, ..3];
pub type Point4<T> = [T, ..4];

fn perlin2_fast<T: Float>(seed: &Seed, point: &Point2<T>) -> f32;
fn perlin2_best<T: Float>(seed: &Seed, point: &Point2<T>) -> f32;
fn perlin3_fast<T: Float>(seed: &Seed, point: &Point3<T>) -> f32;
fn perlin3_best<T: Float>(seed: &Seed, point: &Point3<T>) -> f32;
fn perlin4_fast<T: Float>(seed: &Seed, point: &Point4<T>) -> f32;
fn perlin4_best<T: Float>(seed: &Seed, point: &Point4<T>) -> f32;

fn brownian2<T, F>(seed: &Seed, point: &Point2<T>, noise_func: F, wavelength: f32, octaves: u32) -> f32
    where T: Float, F: Fn(&Seed, &Point2<T>) -> f32;
fn brownian3<T, F>(seed: &Seed, point: &Point3<T>, noise_func: F, wavelength: f32, octaves: u32) -> f32
    where T: Float, F: Fn(&Seed, &Point3<T>) -> f32;
fn brownian4<T, F>(seed: &Seed, point: &Point4<T>, noise_func: F, wavelength: f32, octaves: u32) -> f32
    where T: Float, F: Fn(&Seed, &Point4<T>) -> f32;
~~~

Coming soon
-----------

~~~rust
fn open_simplex2<T: Float>(seed: &Seed, point: &Point2<T>) -> f32;
fn open_simplex3<T: Float>(seed: &Seed, point: &Point3<T>) -> f32;
fn open_simplex4<T: Float>(seed: &Seed, point: &Point4<T>) -> f32;

fn worley2_points<T: Float>(seed: &Seed, point: &Point2<T>) -> [Point2<T>, ..9];
fn worley3_points<T: Float>(seed: &Seed, point: &Point3<T>) -> [Point3<T>, ..27];
fn worley4_points<T: Float>(seed: &Seed, point: &Point4<T>) -> [Point4<T>, ..81];

fn worley2_nearest_point<T: Float>(seed: &Seed, point: &Point2<T>) -> f32;
fn worley3_nearest_point<T: Float>(seed: &Seed, point: &Point3<T>) -> f32;
fn worley4_nearest_point<T: Float>(seed: &Seed, point: &Point4<T>) -> f32;

fn worley2_nearest_edge<T: Float>(seed: &Seed, point: &Point2<T>) -> f32;
fn worley3_nearest_edge<T: Float>(seed: &Seed, point: &Point3<T>) -> f32;
fn worley4_nearest_edge<T: Float>(seed: &Seed, point: &Point4<T>) -> f32;

fn worley2_manhattan_point<T: Float>(seed: &Seed, point: &Point2<T>) -> f32;
fn worley3_manhattan_point<T: Float>(seed: &Seed, point: &Point3<T>) -> f32;
fn worley4_manhattan_point<T: Float>(seed: &Seed, point: &Point4<T>) -> f32;

fn worley2_manhattan_edge<T: Float>(seed: &Seed, point: &Point2<T>) -> f32;
fn worley3_manhattan_edge<T: Float>(seed: &Seed, point: &Point3<T>) -> f32;
fn worley4_manhattan_edge<T: Float>(seed: &Seed, point: &Point4<T>) -> f32;
~~~