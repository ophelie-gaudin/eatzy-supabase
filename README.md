# Eatzy Supabase Project

This is a local Supabase setup for the Eatzy application, a food and meal planning platform.

## Prerequisites

-   [Supabase CLI](https://supabase.com/docs/guides/cli)
-   [Docker Desktop](https://www.docker.com/products/docker-desktop/)
-   [Git](https://git-scm.com/downloads)

## Getting Started

1. Clone this repository:

    ```
    git clone <your-repository-url>
    cd eatzy-supabase
    ```

2. Start the local Supabase development environment:

    ```
    supabase start
    ```

3. Access the Supabase Studio at:
    - http://localhost:54333

## Port Configuration

This project is configured to use the following ports to avoid conflicts:

-   API: 54340
-   Database: 54330
-   Studio: 54333
-   Inbucket: 54334
-   Analytics: 54337

If you encounter port conflicts, you can modify these values in `supabase/config.toml`.

## Database Structure

The Eatzy database includes the following main tables:

-   **profiles**: User profiles with personal information
-   **diets**: Diet types (e.g., vegetarian, vegan)
-   **food_preferences**: User's dietary preferences, allergies, and dislikes
-   **meals_plans**: Generated meal plans for users
-   **recipes**: Recipe information including ingredients and steps
-   **saved_recipes**: Mapping of saved recipes by users
-   **profiles_links**: Relationships between profiles for meal companions

## Development Workflow

1. Make local changes to the database schema using Supabase Studio or by editing migration files
2. Test changes locally with your application
3. Push schema changes to the remote Supabase project when ready

### Creating Migrations

To create a new migration:

```
supabase migration new <migration_name>
```

This creates a new migration file in the `supabase/migrations` directory.

### Applying Migrations

To apply migrations locally:

```
supabase db reset
```

To apply migrations to the remote database:

```
supabase db push
```

## Connecting to your Supabase Project

To link this local project with your online Supabase project:

```
supabase link --project-ref <your-project-ref>
```

## Pulling Remote Changes

To pull schema changes from your remote Supabase project:

```
supabase db pull
```

## Pushing Local Changes

To push local schema changes to your remote Supabase project:

```
supabase db push
```

## Auth and Storage

To pull the auth and storage schemas:

```
supabase db pull --schema auth,storage
```

## Troubleshooting

If you encounter issues with authentication during `supabase db pull` or `supabase db push`:

1. Ensure you're using the correct project reference ID
2. Check your database password in the Supabase dashboard
3. Repair migrations if needed:
    ```
    supabase migration repair --status applied <migration_id>
    ```

## API Access

Local API endpoints are available at:

-   REST API: http://localhost:54340/rest/v1/
-   GraphQL: http://localhost:54340/graphql/v1
-   Auth API: http://localhost:54340/auth/v1/

Access keys for local development can be found after running `supabase start`.
